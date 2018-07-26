### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument můžou zobrazovat další řádek textu

|   |   |
|---|---|
|Podrobnosti|V některých případech <xref:System.Windows.Documents.FlowDocument> elementu se zobrazí další řádek textu při spuštění v rozhraní .NET Framework 4.5 ve srovnání s způsob zobrazení při spuštění v rozhraní .NET Framework 4.0. Nejsou žádné známé případy změny způsobující jakýkoli text, který se má zobrazit nesprávně nebo illegibly, ale může způsobit text, který se zobrazí, která dříve byla vynechána z <xref:System.Windows.Documents.FlowDocument>v zobrazení.|
|Návrh|V některých případech můžete zmenšit vlastnost PageHeight zobrazení elementu jednou obnovit předchozí počet zobrazených řádků.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

