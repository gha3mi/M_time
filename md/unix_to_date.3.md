### NAME

**unix_to_date(3f)** \- [M_time] converts Unix Epoch Time to DAT date-time array **(LICENSE:PD)**

### SYNOPSIS

>     subroutine **unix_to_date**(unixtime,dat,ierr)
>         real(kind=realtime),intent(in) :: unixtime ! Unix time (seconds)
>         integer,intent(out)            :: dat(8)   ! date and time array
>         integer,intent(out)            :: ierr     ! 0 for successful execution


### DESCRIPTION

Converts a Unix Epoch Time (UET) to a DAT date-time array.

### OPTIONS

> unixtime

>

> The "Unix Epoch" time, or the number of seconds since 00:00:00 on January
1st, 1970, UTC; of type **real**(kind=realtime).

### RETURNS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f).

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

ierr

Error code. If 0 no error occurred.

### EXAMPLE

Sample program:

>         program demo_unix_to_date
>         use M_time, only : unix_to_date, u2d, fmtdate, realtime
>         implicit none
>         real(kind=realtime)           :: unixtime
>         real(kind=realtime),parameter :: DAY=86400.0d0 ! seconds in a day
>         integer                       :: dat(8)
>         integer                       :: ierr
>            unixtime=1468939038.4639933d0            ! sample Unix Epoch time
>            call unix_to_date(unixtime,dat,ierr)     ! create DAT array for today
>            write(*,*)'Sample Date=',fmtdate(dat)
>            call unix_to_date(unixtime-DAY,dat,ierr) ! go back one day
>            write(*,*)'Day Before =',fmtdate(dat)    ! subtract day and print
>            call unix_to_date(unixtime+DAY,dat,ierr) ! go forward one day
>            write(*,*)'Day After  =',fmtdate(dat)    ! add day print
>         end program demo_unix_to_date

results:

>         Sample Date=Tuesday, July 19th, 2016 10:37:18 AM
>         Day Before =Monday, July 18th, 2016 10:37:18 AM
>         Day After  =Wednesday, July 20th, 2016 10:37:18 AM
