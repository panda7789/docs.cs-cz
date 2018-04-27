### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Vlastnost CheckForOverflowUnderflow na WinForm je nyní pro System.Drawing hodnotu true.

|   |   |
|---|---|
|Podrobnosti|Vlastnost CheckForOverflowUnderflow pro sestavení System.Drawing.dll je nastavena na hodnotu true.|
|Návrh|Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení. Teď <xref:System.OverflowException?displayProperty=name> je vyvolána výjimka.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

