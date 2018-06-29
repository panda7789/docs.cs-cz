### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>WPF TextBox vybraný text se zobrazí barvu, když je neaktivní textového pole

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, když je neaktivní ovládací prvek WPF textové pole (nemá fokus), zobrazí vybraný text v poli se zobrazí barvu než při řízení je aktivní.|
|Návrh|Předchozí chování (rozhraní .NET Framework 4.0) může být obnoven nastavením <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnost <code>false</code>.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

