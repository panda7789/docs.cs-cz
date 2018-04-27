### <a name="aspnet-accessibility-improvement-in-net-471"></a>Zlepšování usnadnění ASP.NET v rozhraní .NET 4.7.1

|   |   |
|---|---|
|Podrobnosti|ASP.NET je zvýšení fungování ovládacích prvků ASP.NET pomocí technologie usnadnění v sadě Visual Studio lepší podporu ASP.NET zákazníkům.  Mezi ně patří následující změny:<ul><li>Změny implementace vzorů usnadnění chybějící uživatelského rozhraní v ovládacích prvcích, jako například dialogové okno Přidat pole v Průvodci zobrazení podrobností.</li><li>Změny ke zlepšení zobrazení v režimu vysokého kontrastu, jako je Pager pole editoru služby Data.</li><li>Změny ke zlepšení navigační klávesnice vyskytne pro ovládací prvky, jako je okno Konfigurace kontextu objektu nebo okno Konfigurace zdroje dat.</li></ul>|
|Návrh|**Postup aktivování nebo zrušení těchto změn** aby návrháři sady Visual Studio moct využívat tyto změny, musí běžet na rozhraní .NET Framework 4.7.1 nebo novější. Webová aplikace využívat tyto změny v některém z následujících způsobů:<ul><li>Nainstalujte Visual Studio 2017 15.3 nebo novější, který podporuje nové funkce pro usnadnění přístupu s přepínačem následující AppContext ve výchozím nastavení.</li><li>Vyjádření výslovného nesouhlasu chování starší verze usnadnění přidáním **Switch.UseLegacyAccessibility** AppContext přepínač tak, aby `<runtime>` část v devenv.exe.config souboru a jeho nastavení na hodnotu `false`, jako v následujícím příkladu Zobrazuje.</li></ul><pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;<br />&lt;configuration&gt;<br />&lt;runtime&gt;<br />...</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna orientace|
