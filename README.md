# recodecs101

## week 2 practice 按照天数算年龄
<pre>
<code>
# By Websten from forums
#
# Given your birthday and the current date, calculate your age in days. 
# Account for leap days. 
#
# Assume that the birthday and current date are correct dates (and no 
# time travel). 
#

# 判断是否是闰年(润年每年366天 平年每年365天)
def leap_year(year):
    if (year % 400 == 0 or (year % 4 == 0 and year % 100 != 0)):
        return True
    return False

def daysBetweenDates(year1, month1, day1, year2, month2, day2):
    date1 = (month1 - 1) * 30 + day1 # 获取在 year1 年里的天数(假设每月的天数为 30 天)
    date2 = (month2 - 1) * 30 + day2 + (year2 - year1) * 365 # 获取在 year2 年的天数和这些年相隔的天数(假设每年的天数为 365 天 每月的天数为 30 天)
    
    if (leap_year(year1)):
        if (month1 > 2):
            date1 = date1 + 1
    
    year = year1
    while (year < year2):
        if (leap_year(year)):
            date2 = date2 + 1
        year = year + 1
    
    if (leap_year(year2)):
        if (month2 > 2):
            date2 = date2 + 1
            
    month = 1
    while (month < month1):
        if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10):
            date1 = date1 + 1
        if (month == 2):
            date1 = date1 - 2
        month = month + 1
        
    month = 1
    while (month < month2):
        if (month == 1 or month == 3 or month == 5 or month == 7 or month == 8 or month == 10):
            date2 = date2 + 1
        if (month == 2):
            date2 = date2 - 2
        month = month + 1
    age = date2 - date1
    return age

# Test routine

def test():
    test_cases = [((2012,1,1,2012,2,28), 58), 
                  ((2012,1,1,2012,3,1), 60),
                  ((2011,6,30,2012,6,30), 366),
                  ((2011,1,1,2012,8,8), 585 ),
                  ((1900,1,1,1999,12,31), 36523)]
    for (args, answer) in test_cases:
        result = daysBetweenDates(*args)
        if result != answer:
            print "Test with data:", args, "failed"
        else:
            print "Test case passed!"

test()

</code>
</pre>
