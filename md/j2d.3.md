### NAME

**j2d(3f)** \- [M_time] given a JED (Julian Ephemeris Date) returns a date- time array DAT. **(LICENSE:PD)**

### SYNOPSIS

>     function **j2d**(_julian_) result (_dat_)
>         real(kind=realtime),intent(in),optional :: julian
>         integer                                 :: dat(8)

### DESCRIPTION

Converts a Julian Ephemeris Date to a DAT date-time array.

### OPTIONS

> julian

> A Julian Ephemeris Date (JED) is the number of days since noon (not
midnight) on January 1st, 4713 BC. If not present, use current time.

### RETURNS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f).

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

### EXAMPLE

Sample program:

>         program demo_j2d
>         use M_time, only : j2d, d2j, fmtdate, realtime
>         implicit none
>         real(kind=realtime) :: today
>         integer :: dat(8)
>            call date_and_time(values=dat) ! get the date using intrinsic
>            today=d2j(dat)                  ! convert today to Julian Date
>            write(*,*)'Today=',fmtdate(j2d(today))
>            ! math is easy with Julian Days and Julian Dates
>            write(*,*)'Yesterday=',fmtdate(j2d(today-1.0d0))
>            write(*,*)'Tomorrow=',fmtdate(j2d(today+1.0d0))
>         end program demo_j2d

results:

>         Today=Tuesday, July 19th, 2016 08:48:20 AM
>         Yesterday=Monday, July 18th, 2016 08:48:20 AM
>         Tomorrow=Wednesday, July 20th, 2016 08:48:20 AM
