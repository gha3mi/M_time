### NAME

**date_to_julian(3f)** \- [M_time] converts DAT date-time array to Julian Date **(LICENSE:PD)**

### SYNOPSIS

>     subroutine **date_to_julian**(dat,juliandate,ierr)
>         integer,intent(in)               :: dat(8)
>         real(kind=realtime),intent(out)  :: juliandate
>         integer,intent(out)              :: ierr

### DESCRIPTION

> Converts a DAT date-time array to a Unix Epoch Time (UET) value. UET is the
number of seconds since 00:00 on January 1st, 1970, UTC.

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

> juliandate

>

> A Julian Ephemeris Date (JED) is the number of days since noon (not
midnight) on January 1st, 4713 BC.

>

> ierr

> Error code. If 0 no error occurred.

### EXAMPLE

> Sample Program:

>  
>  
>         program demo_date_to_julian

>         use M_time, only : date_to_julian,realtime

>         implicit none

>         integer             :: dat(8)

>         real(kind=realtime) :: juliandate

>         integer             :: ierr

>            ! generate DAT array

>            call date_and_time(values=dat)

>            ! show DAT array

>            write(*,'(" Today is:",*(i0:,":"))')dat

>            ! convert DAT to Julian Date

>            call date_to_julian(dat,juliandate,ierr)

>            write(*,*)'Julian Date is ',juliandate

>            write(*,*)'ierr is ',ierr

>         end program demo_date_to_julian

>  
>  
>  
>

> results:

>  
>  
>         Today is:2016:7:19:-240:11:3:13:821

>         Julian Date is    2457589.1272432986

>         ierr is            0

>  
>  
>  

