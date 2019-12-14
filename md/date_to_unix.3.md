### NAME

**date_to_unix(3f)** \- [M_time] converts DAT date-time array to Unix Epoch Time **(LICENSE:PD)**

### SYNOPSIS

>     subroutine **date_to_unix**(dat,unixtime,ierr)
>         integer,intent(in)               :: dat(8)
>         real(kind=realtime),intent(out)  :: unixtime
>         integer,intent(out)              :: ierr

### DESCRIPTION

> Converts a DAT date-time array to a UET (Unix Epoch Time).

### OPTIONS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f).

>  
>  
>
dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

>  

### RETURNS

> unixtime

>

> The "Unix Epoch" time, or the number of seconds since 00:00:00 on January
1st, 1970, UTC.

>

> ierr

> Error code. If 0 no error occurred.

### EXAMPLE

> Sample program:

>  
>  
>         program demo_date_to_unix

>         use M_time, only : date_to_unix, realtime

>         implicit none

>         integer             :: dat(8)

>         real(kind=realtime) :: unixtime

>         integer             :: ierr

>            call date_and_time(values=dat)

>            write(*,'(" Today is:",*(i0:,":"))')dat

>            call date_to_unix(dat,unixtime,ierr)

>            write(*,*)'Unix Epoch time is ',unixtime

>            write(*,*)'ierr is ',ierr

>         end program demo_date_to_unix

>  
>  
>  
>

> results:

>  
>  
>         Today is:2016:7:18:-240:23:44:20:434

>         Unix Epoch time is    1468899860.4340105

>         ierr is            0

>  

### AUTHOR

