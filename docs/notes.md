# ::
:: is PHP's scope resolution operator — it calls a static method, meaning you call it on the class itself, not on an instance. Compare:

# ->
User::all();       // static method — no object needed, called on the class
$user->delete();   // instance — called on a specific object $user


# $variable
A variable must start with the $ sign, followed by the name of the variable 

# data types

PHP supports the following :

string (text values)
int (whole numbers)
float (decimal numbers)
bool (true or false)
array (multiple values)
object (stores data as objects)
null (empty variable)
resource (references external resources)