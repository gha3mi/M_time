### NAME

**julian_to_date(3f)** \- [M_time] converts a **JED**(Julian Ephemeris Date) to a DAT date-time array. **(LICENSE:PD)**

### SYNOPSIS

>     subroutine **julian_to_date**(julian,dat,ierr)
>         real(kind=realtime),intent(in) :: julian
>         integer,intent(out)            :: dat(8)
>         integer,intent(out)            :: ierr

### DESCRIPTION

Converts a Unix Epoch Time (UET) value to a DAT date-time array. UET is the
number of seconds since 00:00 on January 1st, 1970, UTC.

### OPTIONS

> julian

> Julian Date (days)

> dat

Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f).

> ier

> 0 for successful execution

dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

>  

### RETURNS

> unixtime

The "Unix Epoch" time, or the number of seconds since 00:00:00 on January
1st, 1970, UTC.

> ierr

> Error code. If 0 no error occurred.

### EXAMPLE

Sample program:

>         program demo_julian_to_date
>         use M_time, only : julian_to_date, fmtdate, realtime
>         implicit none
>         real(kind=realtime)     :: juliandate
>         integer                 :: dat(8)
>         integer                 :: ierr
>            ! set sample Julian Date
>            juliandate=2457589.129d0
>            ! create DAT array for this date
>            call julian_to_date(juliandate,dat,ierr)
>            write(*,*)'Sample Date=',fmtdate(dat)
>            ! go back one day
>            call julian_to_date(juliandate-1.0d0,dat,ierr)
>            write(*,*)'Day Before =',fmtdate(dat)
>            ! go forward one day
>            call julian_to_date(juliandate+1.0d0,dat,ierr)
>            write(*,*)'Day After  =',fmtdate(dat)
>         end program demo_julian_to_date

results:

>         Sample Date=Tuesday, July 19th, 2016 11:05:45 AM UTC-04:00
>         Day Before =Monday, July 18th, 2016 11:05:45 AM UTC-04:00
>         Day After  =Wednesday, July 20th, 2016 11:05:45 AM UTC-04:00
