### NAME

**d2j(3f)** \- [M_time] given DAT date-time array returns Julian Date **(LICENSE:PD)**

### SYNOPSIS

>     function **d2j**(_dat_) result (_julian_)
>         integer,intent(in)  :: dat(8)
>         real(kind=realtime) :: julian

### DESCRIPTION

### OPTIONS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f). If not present, use current
time.

> _dat_=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

### RETURNS

> julian

> The Julian Date.

### EXAMPLE

> Sample program:

>         program demo_d2j
>         use M_time, only : d2j
>         implicit none
>         integer :: dat(8)
>            call date_and_time(values=dat)
>            write(*,'(" Today is:",*(i0:,":"))')dat
>            write(*,*)'Julian Date is ',d2j(dat)
>         end program demo_d2j

results:

>         Today is:2016:7:19:-240:2:11:50:885
>         Julian Date is    2457588.7582278359


