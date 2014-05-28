Classes hold data, have methods that interact with that data, and are used to instantiate objects.

Object is an instance of a class.

Modules serve as a mechanism for namespaces and multiple inheritance via mix-ins; and cannot be instantiated.

All methods, no matter the access control, can be accessed within the class. But what about outside callers?

- Public methods enforce no access control -- they can be called in any scope.

- Protected methods are only accessible to other objects of the same class.

- Private methods are only accessible within the context of the current object.

Three ways to invoke a method:  dot operator (or period operator), the Object#send method, or method(:foo).call
	
	object = Object.new
	object.send(:object_id)
		["foo", "bar"].each do |method|
			MyClass.send(method)
		end
	object.method(:object_id).call

Self: at the class level, self is the class. At the instance level, self is the instance in context.

	a || a = b
	// a = b when a == false, otherwise a remains unchanged

Procs are anonymous methods (or nameless functions) that can be passed around like any other object. They are created by Proc.new and blocks (invoked by the yield keyword).

Gems are packaged Ruby applications or libraries

How MVC works: Request first comes to the controller, controller finds and appropriate view, your view interacts with model, model interacts with your database

ORM stands for Object-Relationship-Model, it means that your Classes are mapped to table in the database, and Objects are directly mapped to the rows in the table

Session: are used to store user information on the server side.

Cookies: are used to store information on the browser side or we can say client side

To define a method dynamically: 

	class Message
		[:hello, :goodbye].each do |method_name|
			define_method method_name do |arg|
				“#{method_name} #{arg}”
			end
		end
	end

Constructors are declared as the method initialize

Method overloading is simply multiple methods with same name but different signatures/parameters. 

In the case of Ruby method overloading is not supported. However, it does support the overall goal of passing variable number of parameters to the same method. You would implement it like this:

	class MyClass  
  		def initialize(*args)  
    		if args.size < 2  || args.size > 3  
      			puts 'This method takes either 2 or 3 arguments'  
   		 	elsif  args.size == 2  
        		puts 'Found two arguments'  
      		else  
        		puts 'Found three arguments'  
      		end  
    	end    
	end 
	
Distructive methods are used to change the object value permanently by itself using bang (!) operator

You use load() to execute code, and you use require() to import libraries.

nil cannot be a value, where as a false can be a value

Rake is command line utility of rails

Ruby ships with i18n which is an internationalization gem. 

You need to create locale files and save them under the config/locales directory as: en.yml, es.yml, fr.yml

Partial code:
	
	before_filter :set_locale

 		def set_locale
   			I18n.locale = params[:locale]
 		end

 		def default_url_options(options={})
   			{:locale => I18n.locale}
 		end
 		
Flash is simply a way to pass some value to the next action. 
 
Eager loading is a great optimization strategy to reduce the number of queries that are made against the DB.
	
	clients = Client.includes(:address).limit(10)

A polymorphic association is what one would call “open-ended” association of one class with multiple objects. 

	class Picture < ActiveRecord::Base
  		belongs_to :imageable, :polymorphic => true
	end
 
	class Employee < ActiveRecord::Base
  		has_many :pictures, :as => :imageable
	end
	
Partials and locals:
	
	<%= render partial: "form", locals: {zone: @zone} %>
	
	or
	
	<%= render partial: "customer", object: @new_customer %>
	//Within the customer partial, the customer variable will refer to @new_customer from the parent view.
	
	or 
	
	<%= render partial: "product", collection: @products %>
	
	or
	
	<%= render partial: "product", collection: @products, as: :item %>
	//With this change, you can access an instance of the @products collection as the item local variable within the partial.
	
Fragment caching:
	
	<% CACHE DO %>
	<% end %>

Page caching:

	class ProductsController < ActionController
   		CACHES_PAGE:index
   	end

Scopes are nothing more than SQL scope fragments. 

	scope :recent, :order => "posts.published_at DESC"

include : mixes in specified module methods as instance methods in the target class

extend : mixes in specified module methods as class methods in the target class