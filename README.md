pimtools - converting PIM data formats (vcard, ical etc.)

Often an PIM (personal information manager) application claims to be able to
import or export in a standard format. But when you look closer you realize
that it interpret fields in another way as it is defined in the standard, e.g.
the date format is different or another default charset is assumed.

In the last couple of years I had many of such cases where I needed to hack a
script to tweak the exported data of one application so it can be imported into
another one.

In this repository you can find some of these scripts. Note that I have not
extensively tested the code. It "just worked" in this very situation / with
this specific version number. Note also that the output may not be standard
compatible. If all programms would behave like the standard there would be no
need for conversion scripts ...


ical_jpilot_to_egw.py
=====================

Converts the ical output of jpilot to something which can be imported into
eGroupware. The main problem is the different interpretation of recurrent
events.


vcf_jpilot_to_android.py
========================

Converts the VCARD output of jpilot so that it can be imported with the android
contacts app (cyanogenmod 6.1.1 for N1). This script was necessary due to the
custom birthday field of jpilot and the declaration of the email address as
telefone number.


jpilot_vcard_to_gammu_nokia_2730.py
===================================

Script I used previously to the switch to android to convert the jpilot VCARD
output to something gammu and the Nokia 2730 understood.


vcf_egw_to_gammu_nokia_2730.py
==============================

Tweaks eGroupware's VCARD export so that it can be imported into a Nokia 2730
classic phone with help of gammu. To connect to the phone use the connection
type "bluephonet".  Serial connections over USB raised errors when trying to
download the phonebook.

Tried with gammu 1.26.1 / Wammu 0.32.1, egroupware 1.8.001 and Nokia firmware
10.40 .

Known bugs:
 * Postal addresses cannot be imported (gammu / Nokia issue)
 * Note fields are somehow corrupted and cut off after linebreak (egw issue)
 * birthdays cannot be imported (gammu / Nokia issue).
 * Import takes loooong time. E.g. plan 5 min for 135 contacts.


vcf_egw_to_muttalias.py
=======================

Converts the VCARD export of EGroupware to an mutt alias file. Multiple
addresses are supported. The alias line look like the following example:

    alias muellerhans Hans Mueller <hans.mueller@domain.com>
    alias muellerhans2 Hans Mueller <hansi@domain.com>
