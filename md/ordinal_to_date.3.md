### NAME

**ordinal_to_date(3f)** \- [M_time] when given a valid year and day of the year returns the DAT array for the date **(LICENSE:PD)**

### SYNOPSIS

>     subroutine **ordinal_to_date**(_yyyy_, _ddd_, _dat_)
>           integer, intent(in)   :: yyyy
>           integer, intent(in)   :: ddd
>           integer, intent(out)  :: dat

### DESCRIPTION

> When given a valid year, YYYY, and day of the year, DDD, returns the date as
a DAT date array

### OPTIONS

> yyyy

> known year

> ddd

> known ordinal day of the year

### RETURNS

> dat

> DAT array describing the date

### EXAMPLE

Sample program:

>        program demo_ordinal_to_date
>        use M_time, only : ordinal_to_date
>        implicit none
>        INTEGER            :: yyyy, ddd, mm, dd
>        integer            :: dat(8)
>        integer            :: ios
>          INFINITE: do
>             write(*,'(a)',advance='no')'Enter year YYYY and ordinal day of year DD '
>             read(*,*,iostat=ios)yyyy,ddd
>             if(ios.ne.0)exit INFINITE
>             ! recover month and day from year and day number.
>             call ordinal_to_date(yyyy, ddd, dat)
>             mm=dat(2)
>             dd=dat(3)
>             write(*,*)'MONTH=',mm,' DAY=',dd
>           enddo INFINITE
>        end program demo_ordinal_to_date
