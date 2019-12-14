### NAME

**box_month(3f)** \- [M_time] create specified month in a character array
**(LICENSE:PD)**

### SYNOPSIS

>     subroutine **box_month**(dat,calen)
>     integer,intent(in)    :: dat(8)
>     character(len=21)     :: calen(8)

### DESCRIPTION

**box_month**(3f) uses a year and month from a date array to populate a
small character array with a calendar representing the month.

### OPTIONS

> dat

"DAT" array (an integer array of the same format as the array returned by
the intrinsic **DATE_AND_TIME**(3f)) describing the date to be used to specify
what calendar month to produce.

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

### RETURNS

> calen
> returned character array holding a display of the specified month

### EXAMPLE

Sample program:

>         program demo_box_month
>         use M_time, only : box_month
>         implicit none
>         integer           :: dat(8)
>         character(len=21) :: calendar(8)
>            call date_and_time(values=dat)
>            call box_month(dat,calendar)
>            write(*,'(a)')calendar
>         end program demo_box_month

results:

>                July 2016
>
>           Mo Tu We Th Fr Sa Su
>                        1  2  3
>            4  5  6  7  8  9 10
>           11 12 13 14 15 16 17
>           18 19 20 21 22 23 24
>           25 26 27 28 29 30 31

