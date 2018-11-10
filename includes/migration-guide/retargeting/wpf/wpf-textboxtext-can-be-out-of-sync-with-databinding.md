### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>Pole TextBox.Text ve WPF nemusí být synchronizováno s datovou vazbou

|   |   |
|---|---|
|Podrobnosti|Pokud byla vlastnost <xref:System.Windows.Controls.TextBox.Text> změněna během operace zápisu datové vazby, v některých případech odráží předchozí hodnotu vlastnosti s datovou vazbou.|
|Doporučení|To by nemělo mít žádný negativní dopad. Předchozí chování však můžete obnovit nastavením vlastnosti <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na <code>false</code>.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

