# `self` Discussion Questions

## Instructions

Take 30 minutes and answer the following questions together with your group. Take turns playing around with the code provided in Pry or IRB.

<p align="center">
  <img src="https://curriculum-content.s3.amazonaws.com/module-1/discussion-questions/using-self-in-ruby/Image_110_%20FunnyRobots.png" alt="funny robots" width="300"/>
</p>

1 .   

      class FunnyBots  

        attr_accessor :name, :quotes  

        @@bots = []

        def initialize(name, quotes)
          @name = name
          @quotes = quotes
          @@bots << self
        end

       def random_quote
          self.quotes.sample
        end

        def self.bots
          @@bots
        end

    end

      archer = FunnyBots.new("Archer", ["Danger Zone!", "Read a book", "The cumulative hangover would literally kill me"] )

  A. What is **self** in this line ```@@bots << self``` ?  
        a single instance of a newly created FunnyBot

  B. What is **self** in this line ```self.quotes.sample```?  
        a single instance of a FunnyBot

  C. What kind of **method** is this & what is **self**? ```  def self.bots  
      @@bots end ```  
        class method
        self is still an instance of a class

  D. Will this work ```archer.bots```? If not, why? 
        no, b/c bots is a class method. 
        archer is a instance variable which can only be accessed by an instance method.


2 .

<p align="center">
  <img src="https://curriculum-content.s3.amazonaws.com/module-1/discussion-questions/using-self-in-ruby/Image_111A_Photo%20by%20C%20Drying%20on%20Unsplash.png" alt="Photo by C Drying on Unsplash." width="300"/>
</p>

    class Bicycle

      attr_reader :tire

        def initialize(tire, gears, style)
          @tire = tire
          @gears = gears
          @style = style
        end

        def tire_size
          self.tire
        end

        def self.gears
          @gears
        end


    end

    mongoose = Bicycle.new(4, 10, "BMX")

  For what reasons will the following method calls fail :```mongoose.tire_size = 5```,   ```mongoose.gears```,  ```Bicycle.bikes```, ```Bicycle.styles```? Restructure the class to fix the issues.   

  ```mongoose.tire_size = 5```  ----> tire_size is a reader                                             
       def tire_size=(num)            can't update/change readers
          @tire                             
      end
-or-
      attr_accessor            <----- and get rid of the reader method

  ```mongoose.gears```         ----> gears is a class method, can only respond to Class calls
      def gears                            mongoose is an instance var, can only respond to instance methods
        @gears
      end                      ------> will return gears of that bicycle instance
  -or- add to attr_reader
      attr_reader :tire, :gears

  ```Bicycle.bikes```           ----> there is no bikes method 
-add- 
      @@bikes = []              ----> will store all instances of class

      def initialize(.., .., ..)
        .. ..
        .. ..
        .. ..
        @@bikes << self         ----> will push every .new instance into @@bikes storage bin
      end 

      def self.bikes            ----> will allow class to access/check all instances of class/
        @@bikes                         created bicycle instances stored in the @@bikes array
      end 

  ```Bicycle.styles```          ----> there is no styles method

    def self.styles             ----> will allow class to access/view all styles of all instances
      @style
    end 



<p class='util--hide'>View <a href='https://learn.co/lessons/week-1-day-5-discussion'>Week 1 Day 5 Discussion</a> on Learn.co and start learning to code for free.</p>
