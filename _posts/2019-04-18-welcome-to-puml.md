---
title: "Welcome to PUML!"
date: 2019-04-18 15:34:30 -0400
categories:
  - blog
tags:
  - Processes
  - Jekyll
  - update
---

In PlantUML:

- `->`: Arrow is used for delivery message ...
- `-->`: Dotted Arrow is used for return message

@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: Another authentication Response
@enduml

<img class="plantuml" src="//www.plantuml.com/plantuml/png/nLPjJ-D64FuS_ugfAXIxTRX0TQYA3qHA0eh4YqHykjwdQB4tsCBUFNdNlFpxpgvZZr-WfRrAPo5axymy-ypiCxCvLPeLkimpHqKiup3T_zqPguTKV6C5oo6NGaP98NCEkYYvyvDEEBv7l2WppeH3dWaJyLEHQir5vKecbR1OFgNY7hOiKzmPwrJZLbzayH2p5mXJH5oasoqlk8Wud9SYqgaKZgNcp2wu1jmMB1ZNl817bfLSmHPv0RBEB7GTDG6cL7elU1mppRK1JmMCl-8pkRgQB1QG9BCy7yDM5ZdJFc14b4drNdzqjyGQpu6PY_XrO-0uipLcSqe0nmJcM5CTV6nWQBcT4zhQd-H4QQ0BVP23UOjaAJJQfxJqo8e3NEbiKba5VzOMRsYbs4EqYZBBgaLxJ1kxI_62bivtLO6CHnfCy4RBZUAHQzvZL81Rf-zJYJplmsz7qobMKqiupTbp8ij2iPWPC26HMyQt6foVmzNLSh4wFpUIYCeCMIg8ILPtN3zn8yudQVTM644K6lr09CKZBpJ6CisgNHN7nHW35kbZ6XkrtRs08KNEA52BMWLOYWxc0ePWVUfHmgC7crTTC5f6tzrYgqHdDzTdyz1TV_vZ7TwkhYysg-l5ya-tSn8-Z67imu5dNzfryvqtuaad_UYw_1xOFDgKVIAA3DCjT6d0ITlPC_KGuBvmvJcZaVLkYVCJOVKyHxE-seVIWzOpb7thAq10dYaEhf3l1KUl0IQnjOW2HML94FQ_J74P3bbGyRuZmU-6VZrF--OW-ENoB8J5FBHzrjLHPrSFLjVX3PnkqsVR-07KFL1F7p8vpWfhrtoZaARTYZqbQOOfLg4dnrEJwKnL7O8TRUuGjnbKtawuEqC0JSf2zhGpjuJDLZLCTR50AtuVlknC1TTb8HH8CylXIWfSzE7GVeKbLyPdVt__errOCtGsAqp4S5GjbIQY8O0rxJAgUrwLkPjkNPFBfhert4HcASPkRA77UrydU_baBnvxS8pUTqeNE94sgOZvCzN1D-sCRNtWJpslkYbh6CtkCamvuGM7iseiutYEkKAyyVpoSWn8DnM8wtRCVdUqUoVrJDu1RpDs7y2k5veAVlfeYj1nEkuTS1Knb4RVQpJxsnihg7mgbVw7sKdJpwgNhhV0CSYcnspBTyXE1oJhWuoaYF3mUYT4JKDdr9lRjggKPW33t0-7Sw0x2FeikhfuUxDNQrW5KxtUhjEe7XiZmAU6kLpErw5xKN24KDfrNNDJRyARpNfvPj_jD6bWVABZeNO_s9lMy_6lS_jxrDf4mnwBvlatmsNM_ytJyu5VMmlTaOSFmGzbLnSasFbGhlF5mip7eUxgSDBSGIy3WYNo3V7gPG9uGeQcdOaE7Rd1wCz4alhhS_7_6pgqqOySFCsPsGPzz_Zfd-0bPqg_eTR6sIx-qoNO4MyJsbTnJxn1xwV5K8JDw0bQjtFrVtQx33_VNhVyVZb2DpGwfcdBFFiB">

```plantuml!
@startuml
scale 0.8
!theme cerulean
skinparam handwritten true
skinparam shadowing false
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: Another authentication Response
@enduml
```

```plantuml!
@startuml
scale 0.8
!theme cerulean
skinparam handwritten true
skinparam shadowing false
start
:Get the parameter values from calling function
- assigneddatetime in 'YYYY-MM-DD hh:mm' format, 
- closeddatetime in 'YYYY-MM-DD hh:mm' format,
- starttime in 'hh:mm' format,
- endtime in 'hh:mm' format;

:Set @starttime = starttime
Set @endtime = endtime
Set @assigneddate = assigneddatetime
Set @closeddate = closeddatetime
Set @timecount = 0
Set @timevar1 = @assigneddate
Set @nextdate = @assigneddate
Set @timevar2 = null
Set @param_country = param_country;

:Select time_to_sec(timediff(@endtime,@starttime))/3600 into @maxhoursaday;

note left 
#TIMEDIFF calculates difference between two times
#Time_to_sec function converts data into seconds
#Dividing by 3600 converts the time into hours
end note

:Set @checkstart = null
Set @checkend = null;

:Select CONCAT(SUBSTRING_INDEX(@assigneddate, ' ', 1), ' ',@starttime),
CONCAT(SUBSTRING_INDEX(@closeddate, ' ', 1), ' ',@endtime)  into @checkstart, @checkend;

if (@assigneddate > @checkstart) then (yes)
if (@closeddate < @checkend) then (yes)
    :Set @assigneddate = @assigneddate
    Set @closeddate = @closeddate;
else (no)
    :Set @assigneddate = @assigneddate
    Set @closeddate = @checkend;
endif
else (no)
if (@closeddate < @checkend) then (yes)
    :SET @assigneddate = @checkstart
    Set @closeddate = @closeddate;
else (no)
    :SET @assigneddate = @checkstart
    Set @closeddate = @checkend;
endif
endif

:SELECT DATEDIFF(@closeddate, @assigneddate) INTO @fixcount; 

:Set @count = @fixcount;

If (@fixcount > 0) then (yes)
while (@count>=0)
:select weekday(@nextdate) into @weekday; 
note
    Assign the weekday value to @weekday. Weekday returns o for Monday, 2 for Tuesday ...5 for Saturday and 6 for Sunday
end note
:Select sum(if(date_format(holiday_date,'%Y-%m-%d') = substring_index(@nextdate,' ',1),1,0)) from holiday_table where Country_codes = 'ALL' or instr(Country_codes,@param_country)>0 into @holidayflag; 
if ( @weekday<5 and @holidayflag=0) then (yes)
    if (@count = @fixcount) then (yes)
        :Set @timevar1 = @assigneddate;
        :SELECT CONCAT(SUBSTRING_INDEX(@assigneddate, ' ', 1), ' ',@endtime) INTO @timevar2;

    (no) elseif (@count = 0) then (yes)
        :Select concat(substring_index(@closeddate,' ',1),' ',@starttime) into @timevar1; 
        :Set @timevar2 = @closeddate;
    else (no)
        :Select concat(@nextdate,' ',@starttime) into @timevar1;
        :SELECT CONCAT(@nextdate, ' ', @endtime) INTO @timevar2;
    endif
:SELECT LEAST(Greatest(((TIME_TO_SEC(TIMEDIFF(@timevar2, @timevar1))) / 3600),0),@maxhoursaday) 
INTO @timecounttemp;
:Set @timecount = @timecounttemp + @timecount;
endif

:Set @timevar1 = @nextdate;
:SELECT ADDDATE(SUBSTRING_INDEX(@timevar1, ' ', 1),1) 
INTO @nextdate;
:Set @count = @count - 1;
endwhile
else (no)
:select weekday(@assigneddate) into @weekday; 
:Select sum(if(date_format(holiday_date,'%Y-%m-%d') = substring_index(@assigneddate,' ',1),1,0)) from holiday_table where Country_codes = 'ALL' or instr(Country_codes,@param_country)>0 into @holidayflag; 

if (@weekday<5 and @holidayflag=0) then (yes)
:SELECT Least(Greatest(((TIME_TO_SEC
(TIMEDIFF(@closeddate, @assigneddate))) / 3600),0)
,@maxhoursaday) INTO @timecount;
else (no)
:Set @timecount = 0;
endif
endif
:RETURN @timecount*60;
end
@enduml
```

```plantuml!
@startuml
start
:step 1;
:step 2;
end
@enduml
```

```plantuml!
@startuml
start
:step 1
step 2;
end
@enduml
```
