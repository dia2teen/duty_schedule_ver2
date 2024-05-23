# duty_schedule_ver2
Make a Duty schedule from excel input form
#Anticipated updates

1) May it is possible to make a dataframe including no_additional_duty meaning that the members of this group don't receive duty days anymore.
>> -> Complete this update by Using make a table including members information with one-hot coding. df_mem_info has a row named no_additional_duty. If this row is 1, the duty_score is defined as -100. So, when randomized choice among members, the members of no_additional_duty will not be assigned.

3) Make data of Number and Names of Available members of Each day.
>> -> It will be helpful when master make a list of outside work and making a operation schedule of anesthesiologist of each day.

3) Make a function to control Number of no_holidays of Each member by Master through excel file.

4) Make a function to define ICU duty day befor 2 days from a day when a member hoped
5) Make a holidays dict based on google calendar
>> -> Complete this update by Using API(https://holidays-jp.github.io/) . the name of Function is 'def get_holidays_from_api(year)'


#Input data Master should fill out.

> 1) Fill X 1st ~ 3rd day of members that had a duty day of Last month from the cadidated duty day within 3~4day.

> 2)  Check if the holidays of Japan and Company are correct. If there is wrong, Manipulate the wrong day of holidays in the sheet 'holiday'
>

# Requests that maybe Master can't ask condition

> 1. Number of call duty on holiday of Old boy is limited to 1 day.

>> -> Number of duty on holiday of old boy is limited to 1 day.

> 2. Assembly of Old boy duty duo can't be a pair of duty.

>> -> a member that do icu duty among old boys is only 柴田

>> So, check the icu duty of 柴田's icu duty day if the pair is with old boy.

# Requests from master

1. 上田先生は当直を希望日のみにする
    #->He always applys hoped ICU_duty day. So, He doesn't be need to assign duty day by algorithm.
    ## -> this request is completed by Decreasing of his duty score.
2. 井上先生は週末に当直１回のみに
    #-> Define a call duty by master or make a function to check the X number of each saturday and determine a call duty day that having the most number of X.
    ## -> This request is completed by Deciding a call day prior to assigning and Decreasing of his duty score.
3. Call当直の金曜日も週末潰し扱いにする
    #-> Manipulate function of counting no_holidays of Call duty
    ## -> This request is completed by change the range of no_holidays.
    ## https://colab.research.google.com/drive/1hbFWrvdxeExZWWvb8y4LLuHyJBpHi6rV#scrollTo=5JuETgIxs_oV&line=169&uniqifier=1
4. 北Dr.はCall１回のみに  
    #-> Insert information of Litmitation of Number of duty count to mem_info sheet of input_form excel
        ## -> This request is compledted by Insert of new information, called num_duty.
        ## But, There is a possibility if No addtional duty members don't define their ICU duty
        ## because the number of left duty days is almost equal to Available days of duty of left members.
