### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews AllowCustomPaging na hodnotu nastaveným na hodnotu true může vyvolání události PageIndexChanging při opuštění této poslední stránky zobrazení

|   |   |
|---|---|
|Podrobnosti|Chyba v rozhraní .NET Framework 4.5 způsobuje, že <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> k někdy neaktivuje pro <xref:System.Web.UI.WebControls.GridView?displayProperty=name>s, který jste povolili <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Návrh|Tento problém byl opraven v rozhraní .NET Framework 4.6 a může být kontaktována upgrade na tuto verzi rozhraní .NET Framework. Jako řešení, můžete provést aplikace explicitní BindGrid na žádném <code>Page_Load</code> , by dosáhl tyto podmínky ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> je na poslední stránce a poslední<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> se liší od <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Aplikace můžete případně upravit tak, aby povolit stránkování (namísto vlastní stránkování), jak tento scénář nepředvádí problém.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

