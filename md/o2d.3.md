### NAME

**o2d(3f)** \- [M_time] converts Ordinal day to DAT date-time array **(LICENSE:PD)**

### SYNOPSIS

>     function **o2d**(ordinal,[year]) result (_dat_)
>         integer,intent(in) :: ordinal  ! the day of the year
>         integer,optional   :: year     ! year
>         integer            :: dat(8)   ! date time array

### DESCRIPTION

Given an Ordinal day of the year return a date in the form of a "DAT" array.

### OPTIONS

> ordinal

> The day of the year for the given year, where Jan 1st=1.

> year

> An optional year for the ordinal day. If not present the current year is
assumed.

### RETURNS

> dat

> Integer array holding a "DAT" array, similar in structure to the array
returned by the intrinsic **DATE_AND_TIME**(3f). The timezone value is from
the current time on the current platform.

> dat=[year,month,day,timezone,hour,minutes,seconds,milliseconds]

### EXAMPLE

Sample program:

>         program demo_o2d
>         use M_time, only : o2d,fmtdate
>         implicit none
>         integer :: year
>            do year=2004,2008
>               write(*,*)'100th day of ',year,' is ',fmtdate(o2d(100,year))
>            enddo
>            write(*,*)'100th day of this year is ',fmtdate(o2d(100))
>         end program demo_o2d

results:

>         100th day of 2004 is Friday, April 9th, 2004 00:00:00 PM UTC-02:40
>         100th day of 2005 is Sunday, April 10th, 2005 00:00:00 PM UTC-02:40
>         100th day of 2006 is Monday, April 10th, 2006 00:00:00 PM UTC-02:40
>         100th day of 2007 is Tuesday, April 10th, 2007 00:00:00 PM UTC-02:40
>         100th day of 2008 is Wednesday, April 9th, 2008 00:00:00 PM UTC-02:40
>         100th day of this year is Saturday, April 9th, 2016 00:00:00 PM UTC-02:40

