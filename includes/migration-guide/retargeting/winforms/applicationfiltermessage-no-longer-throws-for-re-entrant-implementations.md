### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage už vyvolá pro vícenásobně implementace IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Podrobnosti|Před rozhraní .NET Framework 4.6.1, volání <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> s <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> který volá <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> nebo <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (při také volání <xref:System.Windows.Forms.Application.DoEvents>) by způsobilo <xref:System.IndexOutOfRangeException?displayProperty=name>.<p/>Počínaje aplikací cílení na rozhraní .NET Framework 4.6.1, toto je vyvolána výjimka, už a vícenásobně výše popsaným způsobem mohou být použity filtry.|
|Návrh|Mějte na paměti, <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> už vyvolá výjimku pro vícenásobně <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> chování popsané výše. To se týká pouze aplikace cílení rozhraní .NET Framework 4.6.1.Apps nebo cílením na rozhraní .NET Framework 4.6.1 může zamítnutí této změny (aplikace cílení starší rozhraní může vyjádřit výslovný souhlas) pomocí [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) přepínač kompatibility.|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

