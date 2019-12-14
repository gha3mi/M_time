### NAME

**mo2v(3f)** \- [M_time] given month name return month number (1-12) of that month **(LICENSE:PD)**

### SYNOPSIS

>
>     function **mo2v**(_month_name_) **result**(_imonth_)
>          character(len=*),intent(in):: month_name ! month name
>          integer                    :: imonth     ! month number

### DESCRIPTION

Given a string representing the name or abbreviation of a Gregorian Calendar
month return a number representing the position of the month in the calendar
starting with 1 for January and ending with 12 for December.

### OPTIONS

> month_name

> name or abbreviation of month. Case is ignored Once enough characters are
found to uniquely identify a month the rest of the name is ignored.

### RETURNS

> imonth

> month number returned. If the name is not recognized a **-1** is returned.

### EXAMPLE

Sample program:

>         program demo_mo2v
>         use M_time, only : mo2v
>         implicit none
>            write(*,*)mo2v("April")
>            write(*,*)mo2v('Apr')
>            ! NOTE: still matches September, as "SE" was enough
>            write(*,*)mo2v('sexember')
>            write(*,*)mo2v('unknown')  ! returns -1
>         end program demo_mo2v

results:

>           >  4
>           >  4
>           >  9
>           > -1
