### NAME

**d2w(3f)** \- [M_time] calculate iso-8601 Week-numbering year date yyyy-Www-d given DAT date-time array **(LICENSE:PD)**

### SYNOPSIS

>     subroutine **d2w**(dat,iso_year,iso_week,iso_weekday,iso_name)
>         integer,intent(in)              :: dat(8)     ! input date array
>         integer,intent(out)             :: iso_year, iso_week, iso_weekday
>         character(len=10),intent(out)   :: iso_name

### DESCRIPTION

> Given a "DAT" array defining a date and time, return the ISO-8601 Week in
two formats -- as three integer values defining the ISO year, week of year and
weekday; and as a string of the form "yyyy-Www-d".

### OPTIONS

> dat

> "DAT" array (an integer array of the same format as the array returned by
the intrinsic **DATE_AND_TIME**(3f)) describing the date, which is the basic
time description used by the other **M_time**(3fm) module procedures.

### RETURNS

> iso_year

> ISO-8601 year number for the given date

> iso_week

> ISO-8601 week number for the given date

> iso_weekday

> ISO-8601 weekday number for the given date

> iso_name

> ISO-8601 Week string for the data in the form "yyyy-Www-d".

### EXAMPLE

Sample program:

> program demo_d2w
> use M_time, only : d2w
> implicit none
> integer           :: dat(8)     ! input date array
> integer           :: iso_year, iso_week, iso_weekday
> character(len=10) :: iso_name
>    call date_and_time(values=dat)
>    call d2w(dat,iso_year,iso_week,iso_weekday,iso_name)
>    write(*,'("ISO-8601 Week:   ",a)')iso_name
>    write(*,'(a,i0)')'ISO-8601 year    ',iso_year
>    write(*,'(a,i0)')'ISO-8601 week    ',iso_week
>    write(*,'(a,i0)')'ISO-8601 weekday ',iso_weekday
> end program demo_d2w

results:

>         ISO-8601 Week:   2016-W29-1
>         ISO-8601 year    2016
>         ISO-8601 week    29
>         ISO-8601 weekday 1

### DEFINITION

The ISO-8601 date and time standard was issued by the International
Organization for Standardization (ISO). It is used (mainly) in government and
business for fiscal years, as well as in timekeeping. The system specifies a
week year atop the Gregorian calendar by defining a notation for ordinal weeks
of the year.

An ISO week-numbering year (also called ISO year informally) has 52 or 53
full weeks. That is 364 or 371 days instead of the usual 365 or 366 days. The
extra week is referred to here as a leap week, although ISO-8601 does not use
this term. Weeks start with Monday. The first week of a year is the week that
contains the first Thursday of the year (and, hence, always contains 4
January). ISO week year numbering therefore slightly deviates from the
Gregorian for some days close to January 1st.

### CALCULATION

The ISO-8601 week number of any date can be calculated, given its ordinal
date (i.e. position within the year) and its day of the week.

### METHOD

Using ISO weekday numbers (running from 1 for Monday to 7 for Sunday),
subtract the weekday from the ordinal date, then add 10. Divide the result by
7\. Ignore the remainder; the quotient equals the week number. If the week
number thus obtained equals 0, it means that the given date belongs to the
preceding (week-based) year. If a week number of 53 is obtained, one must
check that the date is not actually in week 1 of the following year.

These two statements are assumed true when correcting the dates around
January 1st:

  o The number of weeks in a given year is equal to the corresponding week number of 28 December.
  o January 4th is always in the first week.

### ISO_NAME

Week date representations are in the format YYYYWww-D.

  o [YYYY] indicates the ISO week-numbering year which is slightly different
    from the traditional Gregorian calendar year.
  o [Www] is the week number prefixed by the letter W, from W01 through W53.
  o [D] is the weekday number, from 1 through 7, beginning with Monday and
    ending with Sunday.

For example, the Gregorian date 31 December 2006 corresponds to the Sunday of
the 52nd week of 2006, and is written

 >         2006-W52-7 (extended form)
 >         or
 >         2006W527 (compact form).

### REFERENCE

From Wikipedia, the free encyclopedia 2015-12-19

* * *
