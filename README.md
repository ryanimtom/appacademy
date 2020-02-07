# appacademy

class Array
    # require 'byebug'
    def my_each(&prc)
        # debugger
        self.length.times do |i|
            prc.call(self[i])
        end

        self
    end

    def my_select(&prc)
        arr = []
        self.my_each do |ele|
            arr << ele if prc.call(ele) == true 
        end
        arr
    end

    def my_reject(&prc)
        arr = []
        self.my_each do |ele|
            arr << ele if prc.call(ele) == false 
        end
        arr
    end

    def my_any?(&prc)
        self.my_each do |ele|
            return true if prc.call(ele) == true
        end
        false
    end

     def my_all?(&prc)
        self.my_each do |ele|
            return false if prc.call(ele) == false
        end
        true
    end
end

# ## My Each Test ##
# return_value = [1, 2, 3].my_each do |num|
#   puts num
# end.my_each do |num|
#   puts num
# end
# # => 1
#      2
#      3
#      1
#      2
#      3

# p return_value  # => [1, 2, 3]

## my_select test ##
# a = [1, 2, 3]
# p a.my_select { |num| num > 1 } # => [2, 3]
# p a.my_select { |num| num == 4 } # => []

## my_reject test ##
# a = [1, 2, 3]
# p a.my_reject { |num| num > 1 } # => [1]
# p a.my_reject { |num| num == 4 } # => [1, 2, 3]

## my_any? and my_all? ##
a = [1, 2, 3]
p a.my_any? { |num| num > 1 } # => true
p a.my_any? { |num| num == 4 } # => false
p a.my_all? { |num| num > 1 } # => false
p a.my_all? { |num| num < 4 } # => true
