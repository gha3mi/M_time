### NAME

**d2o(3f)** \- [M_time] converts DAT date-time array to Ordinal day **(LICENSE:PD)**

### SYNOPSIS

>     function **d2o**(_dat_) result (_ordinal_)
>         integer,intent(in),optional :: dat(8)   ! date time array
>         integer                     :: ordinal  ! the returned day of the year

### DESCRIPTION

Given a date in the form of a "DAT" array return the Ordinal Day, (ie. "the
day of the year").

### OPTIONS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f).

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]
>  
### RETURNS

> ordinal
> 
> The day of the year calculated for the given input date, where Jan 1st=1.

### EXAMPLE

Sample program:

>         program demo_d2o
>         use M_time, only : d2o
>         implicit none
>         integer :: dat(8)
>            call date_and_time(values=dat)
>            write(*,'(" Today is:",*(i0:,":"))')dat
>            write(*,*)'Day of year is:',d2o(dat)
>            ! year, month, day, timezone, hour, minute, seconds, milliseconds
>            dat=[2020,12,31,-240,12,0,0,0]
>            write(*,*)dat(1),' Days in year is:',d2o(dat)
>            dat=[2021,12,31,-240,12,0,0,0]
>            write(*,*)dat(1),' Days in year is:',d2o(dat)
>            dat=[2022,12,31,-240,12,0,0,0]
>            write(*,*)dat(1),' Days in year is:',d2o(dat)
>            dat=[2023,12,31,-240,12,0,0,0]
>            write(*,*)dat(1),' Days in year is:',d2o(dat)
>            dat=[2024,12,31,-240,12,0,0,0]
>            write(*,*)dat(1),' Days in year is:',d2o(dat)
>         end program demo_d2o

results:

>         Today is:2016:7:19:-240:20:1:19:829
>         Day of year is:         201
>                2020  Days in year is:         366
>                2021  Days in year is:         365
>                2022  Days in year is:         365
>                2023  Days in year is:         365
>                2024  Days in year is:         366
