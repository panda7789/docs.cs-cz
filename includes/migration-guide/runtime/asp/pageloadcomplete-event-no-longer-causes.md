### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Události Page.LoadComplete už způsobí, že System.Web.UI.WebControls.EntityDataSource řízení k vyvolání datová vazba

|   |   |
|---|---|
|Podrobnosti|<xref:System.Web.UI.Page.LoadComplete> Události už způsobí, že <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> řízení k vyvolání datová vazba pro změny parametry pro vytvoření, aktualizace nebo odstranění. Tato změna eliminuje nadbytečné cesty k databázi, zabraňuje hodnoty ovládacích prvků v době resetování a vytváří chování, která je konzistentní s dalšími kontrolami data, jako <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> a <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>. Tato změna vytváří různé chování k nepravděpodobnému aplikací závisí na vyvolání datové vazby v <xref:System.Web.UI.Page.LoadComplete> událostí.|
|Návrh|Pokud je třeba pro datové vazby, ručně vyvolejte databind v událost, která je dříve v po zálohování.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|

