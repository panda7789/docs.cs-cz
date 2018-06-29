### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Občas nepodařilo posuňte nejnižší položku v ItemsControls (např. ListBox a DataGrid) při použití vlastní DataTemplates

|   |   |
|---|---|
|Podrobnosti|V některých případech je příčinou chyby v rozhraní .NET Framework 4.5 ItemsControls (jako je <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>atd) není při použití vlastní DataTemplates posun jejich nejnižší položku. Pokud posouvání dojde k pokusu o podruhé (po posouvání zálohování), nebude pak spolupracovat.|
|Návrh|Tento problém byl opraven v rozhraní .NET Framework 4.5.2 a může být kontaktována upgrade na tuto verzi (nebo novější), rozhraní .NET Framework. Alternativně uživatelé stále můžete přetáhnout posuvníky poslední položky v těchto kolekcích, ale muset zkuste dvakrát Uděláte to tak úspěšně.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|

