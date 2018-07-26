### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Formuláře Windows na CheckForOverflowUnderflow vlastnost má nyní hodnotu true pro System.Drawing

|   |   |
|---|---|
|Podrobnosti|Vlastnost CheckForOverflowUnderflow System.Drawing.dll sestavení je nastavena na hodnotu true.|
|Návrh|Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení. Nyní <xref:System.OverflowException?displayProperty=name> je vyvolána výjimka.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

