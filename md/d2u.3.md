### NAME

**d2u(3f)** \- [M_time] given DAT date-time array returns Unix Epoch Time (UET starts at 0000 on 1 Jan. 1970, UTC) **(LICENSE:PD)**

### SYNOPSIS

>     function **d2u**(_dat_) result (_unixtime_)
>           integer,intent(in),optional :: dat(8)
>           real(kind=realtime)         :: unixtime

### DESCRIPTION

> Converts a DAT date-time array to a Unix Epoch Time value. Typically
mathematical operations such as sums, sorting and comparison are performed
with simple UET numeric values, and then they are converted back.

### OPTIONS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f). If not present the current
time is used

>  
>  
>
dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

>  
>  
>  

### RETURNS

> unixtime

>

> The "Unix Epoch" time, or the number of seconds since 00:00:00 on January
1st, 1970, UTC.

### EXAMPLE

> Sample program:

>  
>  
>         program demo_d2u

>         use M_time, only : d2u

>         implicit none

>         integer           :: dat(8)

>            call date_and_time(values=dat)

>            write(*,'(" Today is:",*(i0:,":"))')dat

>            write(*,*)'Unix Epoch time is ',d2u(dat)

>         end program demo_d2u

>  
>  
>  
>

> results:

>  
>  
>         Today is:2016:7:19:-240:2:0:48:561

>         Unix Epoch time is    1468908048.5610321

>  

### AUTHOR

