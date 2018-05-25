#Object Encapsulation Code Pattern in Javascript 

One of the key benefits of object oriented programming paradigm is that it provides encapsulation of its objects.  Encapsulation allows us to write **robust** code and build **well-behaved** objects. 

1. By encapsulating the object's data in its private area we and therefore make it accidental object's state
2. By only provding access to the object's beahvWe We can define the behavior of the objects through its public methods we provide - making it a very robus cideing unit. 

These are easy to do in Java etc the so called classical or class based langauges. 
Javascript is not that and even the new ES 6 not that sitre. Howeber it is easy to do and a good things by codin in the following pattern


##Guide

think of your object and its data 
think which data needs to be known at creation
access to publcic is read ancce or write access
what other method do you want to give

##Example cats

I want to create cat objects. I want all its data private. The three data 

name, weight and age - name unchanged



```javascript 
  /* the following object literal is only visible within the cat_constructor function */
  var private_cat_data = {
    name: init_props.name,
    weight: init_props.weight,
    age : init_props.age

  }
```


###A skeleton

```javascript 

var cat_constructor = function (init_props)  {


  /* the following object literal is only visible within the cat_constructor function */
  var private_cat_data = {

  }
  // the object the cat constructor will return
  a_cat = {}

  /* getters  do not put things that you do not want seen*/
  
  /*setters */

  /* Note no setters for name, we are assuming each object that will be created will have a permanent name */

  /* other methods object's behavior */

  a_cat.isObese = function () {return private_cat_data.weight>10}




  return a_cat;


}

```

### Filling in the GAP




```javascript
var cat_constructor = function (init_props)  {


  /* the following object literal is only visible within the cat_constructor function */
  var private_cat_data = {
    name: init_props.name,
    weight: init_props.weight,
    age : init_props.age

  }
  // the object the cat constructor will return
  a_cat = {}

  /* getters */
  a_cat.get_name = function () {return private_cat_data.name}
  a_cat.get_age = function () {return private_cat_data.age}
  a_cat.get_weight = function () {return private_cat_data.weight}

  /*setters */

  /* Note no setters for name, we are assuming each object that will be created will have a permanent name */

  a_cat.set_age = function (age) {private_cat_data.age=age}
  a_cat.set_weight = function (weight) {private_cat_data.weight=weight}

  /* other methods */

  a_cat.isObese = function () {return private_cat_data.weight>10}




  return a_cat;


}



/* we can now create cat object and test encapsulation */
var boley_cat = cat_constructor ({name:"boley", age:1, weight:6})
console.log(boley_cat.name) // undefined we do not have access to the private data
console.log(boley_cat.get_name())
boley_cat.set_age(2)
console.log(boley_cat.get_age())
console.log(boley_cat.isObese())
boley_cat.set_weight(8)
console.log(boley_cat.isObese())

/* We can create many cats and put them in an array */

var an_array_of_cats =[]
an_array_of_cats.push (cat_constructor ({name:"foo", age:6, weight:16}))
an_array_of_cats.push (cat_constructor ({name:"bar", age:6, weight:18}))
an_array_of_cats.push (boley_cat) // push boley too
an_array_of_cats.push (cat_constructor ({name:"very old", age:18, weight:19}))




/* Now let's write the function to display name and weight of the obese cats */

for (var c in an_array_of_cats) {
  if (an_array_of_cats[c].isObese()) {
    console.log("%s is fat, %s pounds", an_array_of_cats[c].get_name(), an_array_of_cats[c].get_weight());
  }
}


```

