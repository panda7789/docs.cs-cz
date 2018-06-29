### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument může zobrazovat další řádek s textem

|   |   |
|---|---|
|Podrobnosti|V některých případech <xref:System.Windows.Documents.FlowDocument> element se zobrazí další řádek s textem, při spuštění v rozhraní .NET Framework 4.5 ve srovnání s způsob zobrazení při spuštění v rozhraní .NET Framework 4.0. Neexistují žádné známé případy změnu způsobující jakýkoli text, který se má zobrazit chybně nebo illegibly, ale by mohl způsobit zobrazit text, který byl dříve vynechání z <xref:System.Windows.Documents.FlowDocument>je zobrazení.|
|Návrh|V některých případech můžete snížení element zobrazení PageHeight vlastnost jedním obnovit předchozí počet zobrazených řádků.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

