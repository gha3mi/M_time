### NAME

**guessdate(3f)** \- [M_time] reads in a date, in various formats **(LICENSE:PD)**

### SYNOPSIS

>     subroutine **guessdate**(anot,dat)
>         character(len=*),intent(in) :: anot
>         integer,intent(out)         :: dat(8)

### DESCRIPTION

Read in strings and except for looking for month names remove non-numeric
characters and try to convert a string assumed to represent a date to a date-
time array.

Years should always be expressed as four-digit numbers, and except for the
special format yyyy-mm-dd the day should come after the year. Named months are
preferred. If ambiguous the order is assumed to be day - month - year. Times
are assumed to be of the form HH:MM:SS

It is planned that this routine will be superseded. As an alternative, a C
routine exists in the standard C libraries that allows for expansive features
when reading dates that can be called via the ISO_C_BINDING interface.

### OPTIONS

> anot

> A string assumed to represent a date including a year, month and day.

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f).

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

### EXAMPLE

Sample program:

>         program demo_guessdate
>         use M_time, only : guessdate, fmtdate
>         implicit none
>         character(len=20),allocatable :: datestrings(:)
>         character(len=:),allocatable  :: answer
>         integer                       :: dat(8)
>         integer                       :: i
>            datestrings=[ &
>            & 'January 9th, 2001   ',&
>            & ' Tue Jul 19 2016    ',&
>            & ' 21/12/2016         ',&
>            & ' 4th of Jul 2004    ' ]
>            do i=1,size(datestrings)
>               write(*,'(a)')repeat('-',80)
>               write(*,*)'TRYING ',datestrings(i)
>               call guessdate(datestrings(i),dat)
>               write(*,*)'DAT ARRAY ',dat
>               answer=fmtdate(dat)
>               write(*,*)'FOR '//datestrings(i)//' GOT '//trim(answer)
>            enddo
>         end program demo_guessdate

results:

>         ---------------------------------------------------------------------
>         TRYING January 9th, 2001
>         DAT ARRAY         2001  1  9   -240    0   0   0    0
>         FOR January 9th, 2001    GOT Tuesday, January 9th, 2001 12:00:00 AM
>         ---------------------------------------------------------------------
>         TRYING  Tue Jul 19 2016
>         DAT ARRAY         2016  7  19  -240    0   0   0    0
>         FOR  Tue Jul 19 2016     GOT Tuesday, July 19th, 2016 12:00:00 AM
>         ---------------------------------------------------------------------
>         TRYING  21/12/2016
>         DAT ARRAY         2016  12 21  -240    0   0   0    0
>         FOR  21/12/2016          GOT Wednesday, December 21st, 2016 12:00:00 AM
>         ---------------------------------------------------------------------
>         TRYING  4th of Jul 2004
>         DAT ARRAY         2004  7  4   -240    0   0   0    0
>         FOR  4th of Jul 2004     GOT Sunday, July 4th, 2004 12:00:00 AM
