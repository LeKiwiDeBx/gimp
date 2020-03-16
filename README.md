# gimp
=head1 NAME

import_css_to_gpl - Create a palette from CSS stylesheet

=head1 SYNOPSIS

<Toolbox>/Palette/Import from CSS...

=head1 DESCRIPTION

Create a palette from CSS stylesheet

It's very useful plugin to extract colors from css stylesheet, without being cumbersome and 
making tricky conversion calculations. It's handy plugin in the Gimp which reduce 
lots of work on your part.

=head2    Requirement :

Performs parsed action on css stylesheet conform to rules for CSS3 documents. 
CSS file should have a .css extension.

=head2    Features :

=over 4

=item *

    Parsed css rules below, will be converted into the gpl format :
    using three-digit notation (#RGB) and the six-digit form (#RRGGBB). 
    using rgb() rgba() hsl() hsla() functionnal notations

=item *

    Merge duplicate colors, The contents of the last line comment will be parsed, others discards.

=item *

    Parsed the color keywords and aliases (such as gray/grey) found in CSS3.

=item *

    Parsed color keywords and three and six-digit hex value in different gradient type (linear and radial).

=item *

    Please note that the opacity CSS property value (rgb|hsl)a will be ignored, because is not available in the gpl file.

=item *

    Add six digit hex value color at the begin of the comment line gpl.

=item *

    Add a color keywords which could be matched by r g b, after #RRGGBB of the comment line gpl.

=item *

    Also add a comment at the end of the line gpl, if the end of the line css is commented out.
    i.e. 
    CSS line :  color: #ff0; /*What...is your favorite color? blue, No, yel-- auugh!*/
    the new line should now look like below:
    gpl line :  255 255 0 #FFFF00 yellow What...is your favorite color? blue, No, yel-- auugh!

=back

=head2    Activating the script :

 You can access it from GIMP menu: <Menu bar>  <Palette>  <Import from CSS...> 

=head2    How to work it off ?

    Fill in the fields below :

    [File CSS]  Choose the file css that would be suitable for using extract colors.

    [File GPL]  This is the file name of the palette, using an ASCII special format, which should be file system friendly.(Avoid quotation marks, for example). If the file does not exist, it will create <filename.gpl>. Otherwise, if this field is empty, the file is given the same name as the CSS file <filenameCSS.gpl>.

    [Palette name]  This is the proper name for the palette as shown in the palette chooser dropdown. If the name is omitted, the name is given the same name as the CSS file. If the name you choose is already used by an existing palette, a unique name will be formed by appending a number (e. g., "#1", the default behaviour of GIMP). 

    [Column number] Here you specify the number of columns for the palette. Within the range for this value from 1 to 10.(1 as a default value)

    Then click Ok, and the file gpl is "automagically" generate for you.

=head2    How to Import a Color Palette Into GIMP ?

See GIMP user manual L<https://www.gimp.org/docs/>

=head1 PARAMETERS

    [PF_FILE,   "file_css", "File CSS ",""],
    [PF_FILE, "file_gpl", "File GPL ", ""],
    [PF_STRING, "name", "Palette name ", ""],
    [PF_SPINNER, "column", "Column number ",1,[1,10,1]],
    [PF_RADIO, "model", "Select model ",0,[Rgb=>0,Hsv=>1]],
    [PF_RADIO, "col", "Order by column ", 0,[RH=>0,GS=>1,BV=>2]],
    [PF_BOOL,"order", "Order by ascending ", [ASC=>0,DESC=>1],"TRUE "],

=head1 AUTHOR

</{LeKiwiDeBx}> 
Please feel free to contact me if you have any questions : L<https://github.com/LeKiwiDeBx>

=head1 HISTORY

2020-02-22 v0.0.1 First version.

There are many flaws (probably contain some bugs) in this script-fu: it's slow, ugly (shall Larry bless me)
and not really ergonomic. Indeed, this is part of why we love it.
Enjoy :) 

=head1 DATE

2020-02-22

=head1 LICENSE

Copyright 2020 </{LeKiwiDeBx}>  GNU General Public License

