# `self` Discussion Questions

## Instructions

Take 30 minutes and answer the following questions together with your group. Take turns playing around with the code provided in Pry or IRB.

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
  B. What is **self** in this line ```self.quotes.sample```?  
  C. What kind of **method** is this & what is **self**? ```  def self.bots  
      @@bots end ```  
  D. Will this work ```archer.bots```? If not, why? 
  

2 .

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

  For what reasons will the following method calls fail :```mongoose.tire_size = 5```, ```mongoose.gears```, ```Bicycle.bikes```, ```Bicycle.styles```? Restructure the class to fix the issues.

<p class='util--hide'>View <a href='https://learn.co/lessons/week-1-day-5-discussion'>Week 1 Day 5 Discussion</a> on Learn.co and start learning to code for free.</p>
