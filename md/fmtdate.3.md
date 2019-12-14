### NAME

**fmtdate(3f)** \- [M_time] given DAT date-time array return date as string using specified format **(LICENSE:PD)**

### SYNOPSIS

>     function **fmtdate**(values,format) RESULT (_timestr_)
>         integer,dimension(8),intent(in)      :: values
>         character(len=*),intent(in),optional :: format
>         character(len=:),allocatable         :: timestr

### DESCRIPTION

> The **fmtdate**(3f) procedure lets you reformat a DAT array in many common
formats using a special string containing macro names beginning with '%'. To
see the allowable macros call or see the **fmtdate_usage**(3f) routine.

### OPTIONS

> values

> date in a "DAT" array, which is the same format as the values returned by
the intrinsic **DATE_AND_TIME**(3f).

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

> format

> string describing how to format the "DAT" array. For a complete description
of the formatting macros supported see **fmtdate_usage**(3f).

### RETURNS

> timestr

>

> formatted output string representing date

### EXAMPLE

Sample program:

>         program demo_fmtdate
>         use M_time, only : fmtdate
>         implicit none
>         integer :: dat(8)
>            call date_and_time(values=dat)
>            write(*,*)fmtdate(dat,"current date: %w, %l %d, %Y %H:%m:%s %N")
>            call showme()
>         contains
>         subroutine showme()
>            use M_time, only : fmtdate_usage
>            call fmtdate_usage() ! see all formatting options
>         end subroutine showme
>         end program demo_fmtdate

results:

>           The current date is Sun, Jul 17th, 2016 01:21:35 PM
>            ::
>            :: An up-to-date description of all the
>            :: formatting options will appear here
>            ::
