### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Události Page.LoadComplete již nezpůsobuje, že ovládací prvek System.Web.UI.WebControls.EntityDataSource datovou vazbu

|   |   |
|---|---|
|Podrobnosti|<xref:System.Web.UI.Page.LoadComplete> Událost již nezpůsobuje, že <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> ovládacího prvku na datovou vazbu pro změny vytvoření/aktualizace nebo odstranění parametrů. Tato změna eliminuje nadbytečné cesty k databázi, zabraňuje resetu hodnot ovládacích prvků a vytváří chování, které je konzistentní s jinými ovládacími prvky dat jako <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> a <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>. Tato změna vytváří různé chování v nepravděpodobném případě, že aplikace závislá na vyvolání datové vazby v <xref:System.Web.UI.Page.LoadComplete> událostí.|
|Návrh|Pokud je potřeba pro vázání dat, vyvolejte ručně databind ve událost, která předchází v po obnovení.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|

