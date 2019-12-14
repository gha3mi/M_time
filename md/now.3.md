### NAME

**now(3f)** \- [M_time] return string representing current time given format **(LICENSE:PD)**

### SYNOPSIS

>     function **now**(_format_) RESULT (_timestr_)
>         character(len=*),intent(in)     :: format  ! input format string
>         character(len=:),allocatable    :: timestr ! formatted date

### DESCRIPTION

The **now**(3f) function is a call to the **fmtdate**(3f) function using the
current date and time. That is, it is a convenient way to print the current
date and time.

### OPTIONS

> format

> string describing how to _format_ the current date and time. For a complete
description of the formatting macros supported see **fmtdate_usage**(3f).

### RETURNS

> timestr

> formatted output string representing date

### EXAMPLE

Sample Program:

>         program demo_now
>         use M_time, only : now
>         implicit none
>            write(*,*)now("The current date is %w, %l %d, %Y %H:%m:%s %N")
>            call showme()
>         contains
>         subroutine showme() ! see all formatting options
>         use M_time, only : fmtdate_usage
>            call fmtdate_usage() ! see all formatting options
>         end subroutine showme
>         end program demo_now

results:

>           The current date is Sun, Jul 17th, 2016 01:21:35 PM
>            ::
>            :: description of all formatting options will appear here
>            ::
