RUBY CHEAT SHEET
01/17/2014 Friday


Variables 
- store values

Data types
- FixNum: values cannot be altered
- Float: values cannot be altered
- String: values can be changed. In quotes (but only use double quotes in string interpolation “#{ }”).
	String methods: 
	— concatenation
	— .length
	— .split
- Array: ordered set of values, which can be any datatype and can be accessed by integer indices. In square brackets.
	Array methods:
	— to create an array of strings: y = %w{foo bar bas} = [‘foo’, ‘bar’, ‘bas’]
	— to add things into an array: .push, <<, .unshift
	— to search an array: array[index], or array.index  (i.e. array[0] = array.first)
	— to remove things from an array: .shift, .pop
	— .sort
	— .shuffle

	— Iterating on arrays:
		original array = array.each do |element|          (.each returns the original array)
						puts element
			      		   end
		
		array.each_with_index |element, index|          (.each_with_index will pass through the number of times looped)
			puts “#{index}: #{element}
		end	

		new array = array.map do |element|                  (.map returns a new array after the original was passed through the block)
					element.upcase
				      end

- Hash: sets of key-value pairs. Keys can be strings, symbols, or FixNum. Values can be anything. In curly brackets.
	— can set default value by massing .new any argument
	Hash methods: 
	— to access items in a hash by key = hash[key]    ([:key] != [‘key])
	— to access items in a hash of hashes, chain brackets together
	— to assign value of a key: hash[key] = “value”
	
	— Iterating on hashes:
		hash.each do |key, value|
			puts “#{key} #{value}”
		end

- Boolean: represent ‘true’ and ‘false’

Flow control
- if / unless: most common. 
	‘If’ runs a section of code if the conditional check evaluates to ‘true’
	‘Unless’ runs a section of code if the conditional check evaluates to ‘false’
- while: beware of infinite loops as while loops over something as long as its conditional is true.
		while x < 10
			puts x
			x = x  + 1
		end

- case: should only be used when you have a lot of options (use sparingly)
		button = gets.chomp
		case button
			when ‘a’
				puts ‘a’
			when ‘b’
				puts ‘b’
		end

- conditional expression:
	— compare equality with ==
	— compare for inequality with !=
	— compare for greater than or less than with > and < . Also, greater than or equal to >= and less than or equal to  <=.
	— boolean && and || or
								true && true is true	                                     true || false is true
								true && false is false                                   false || true is true
								false && false is false                                  false || false is false

Methods
- reusable codes, named by snake_casing
- if a local variable is born in the method, it dies in the method
- can only access local variables passed directly to it
- returns the last line of the method (unless there is an explicit ‘return’, which halts and quits the method)

Classes
- named by CamelCase, representing objects, with attributes and behaviors (methods)
- new instance of a class is created by calling ‘new’ on the class, which will run the ‘initialize’ method
- instance variables (@) attach named values to a class
	class Foo
		def initialize(name)
			@name = name
		end
		
		def name
			@name
		end
	end
	
	x = Foo.new(’Dean’)
	x.name = ‘Dean’

- attr_accessor is a shortcut for writing methods to set and get instance variable values