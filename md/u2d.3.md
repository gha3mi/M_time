### NAME

**u2d(3f)** \- [M_time] given Unix Epoch Time returns DAT date-time array **(LICENSE:PD)**

### SYNOPSIS

>     function **u2d**(_unixtime_) result (_dat_)
>         class(*),intent(in),optional      :: unixtime
>         ! integer
>         ! real
>         ! real(kind=realtime)
>         integer                           :: dat(8)

### DESCRIPTION

### OPTIONS

> unixtime

> The "Unix Epoch" time, or the number of seconds since 00:00:00 on January
1st, 1970, UTC. If not present, use current time.

### RETURNS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f).

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

### EXAMPLE

Sample program:

>         program demo_u2d
>         use M_time, only : u2d, d2u, fmtdate, realtime
>         implicit none
>         real(kind=realtime) :: today
>         integer :: dat(8)
>            call date_and_time(values=dat) ! get the date using intrinsic
>            today=d2u(dat)                 ! convert today to Julian Date
>            write(*,*)'Today=',fmtdate(u2d(today))
>            write(*,*)'Yesterday=',fmtdate(u2d(today-86400.0d0)) ! subtract day
>            write(*,*)'Tomorrow=',fmtdate(u2d(today+86400.0d0))  ! add day
>         end program demo_u2d

results:

>         Today=Tuesday, July 19th, 2016 11:10:08 AM
>         Yesterday=Monday, July 18th, 2016 11:10:08 AM
>         Tomorrow=Wednesday, July 20th, 2016 11:10:08 AM

