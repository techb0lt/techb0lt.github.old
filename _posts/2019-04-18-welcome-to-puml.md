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

<object data="{{ site.url }}{{ site.baseurl }}/assets/images/My-mostly-vegetarian-Low-Carbs-Diet.pdf" width="1000" height="1000" type="application/pdf"></object>

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
