### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text může být mimo synchronizace s datovou vazbou

|   |   |
|---|---|
|Podrobnosti|V některých případech <xref:System.Windows.Controls.TextBox.Text> vlastnost odráží předchozí hodnotu hodnoty vlastnosti datové vazby, pokud je vlastnost změněna během operace zápisu datové vazby.|
|Návrh|To by nemělo mít žádný negativní dopad. Předchozí chování však můžete obnovit nastavením <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> vlastnost <code>false</code>.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

