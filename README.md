	===========================================================================
	 _____           __    _ _               _                                 
	|   __|_ _ _____|  |  |_| |_ ___ ___ ___| |                                
	|__   | | |     |  |__| |  _| -_|  _| .'| |                                
	|_____|___|_|_|_|_____|_|_| |___|_| |__,|_| v 0.0.1 (c) 2011 - 2013        
	===========================================================================

# Synopsis #

Wordified numbers for [Marketcircle's Billings Pro](http://www.marketcircle.com/billingspro/) made in [F-Script](http://www.fscript.org).

In certain more advanced reports that are printed you might get a requirement that numbers must be spelled out to avoid forgery. Or, if you just want to impress with the details of invoices\reports you send out, you might actually want to spell it how much a person needs to pay. In any case, this F-Script snippet might help you to accomplish this requirement. It was originally written for Estonian language so if you don’t get 100% correct results then be ready to get your hands dirty. Perhaps this is possible to accomplish in a much simpler way but it works for me. Enjoy.

## Example ##

As an example you have totalSum = 525.25 which with the help of this F-Script will be shown as:

> Five Hundred Twenty Five Euros and 25 Cents

# Installation #

You need to change the first mapping of the field totalSum depending where you place the fields in your report. Please see sumliteral.fscript (line 2) and subunit.fscript (line1). This number assignment must reflect the value you want to wordify and is specific to your report.

sumliteral.fscript:

	totalSum := (element valueForKeyPath:'parent.parent.parent.parent.reportData.object.total') integerPart.

subunit.fscript:

	totalSum := element valueForKeyPath:'parent.parent.parent.parent.reportData.object.total'.

Feel free to change the capitalization of letters to your liking and for British English language users, you need to make modifications to include "and" after hundreds.

1. Create a dynamic text field in your report with 2 special script fields in it (for example)

    “SumLiteral” Euros and “cents” Cents

2. For SumLiteral field enter the contents of sumliteral.fscript (make sure the mathematical expression checkbox is UNchecked and make sure you have changed the totalSum assignment as described in the beginning of the paragraph)

3. For the “cents” part use the contents of subunit.fscript (make sure the mathematical expression checkbox is UNchecked and make sure you have changed the totalSum assignment as described in the beginning of the paragraph)

# Extra thoughts #

You can easily combine the scripts to return both values. Also the script is langauge agnostic so you should be able to easily modify the script to your specific needs of l10n. Rewrite the words and play with spacing to get things just right. In the beginning of the sumliteral.fscript you can assign totalSum a value for testing it in the F-Script shell.

# License #

Copyright (c) 2013, Sten Feldman 
All rights reserved. 

Redistribution and use in source and binary forms, with or without 
modification, are permitted provided that the following conditions are met: 

 * Redistributions of source code must retain the above copyright notice, 
   this list of conditions and the following disclaimer. 
 * Redistributions in binary form must reproduce the above copyright 
   notice, this list of conditions and the following disclaimer in the 
   documentation and/or other materials provided with the distribution. 

THIS SOFTWARE IS PROVIDED BY THE AUTHOR AND CONTRIBUTORS ``AS IS'' AND ANY 
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED 
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE 
DISCLAIMED. IN NO EVENT SHALL THE AUTHOR OR CONTRIBUTORS BE LIABLE FOR ANY 
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR 
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER 
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT 
LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY 
OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH 
DAMAGE. 