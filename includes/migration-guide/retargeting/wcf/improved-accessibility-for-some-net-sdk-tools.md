### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Vylepšené usnadnění pro některé nástroje .NET SDK

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework SDK 4.7.1 byly vylepšeny nástroje svcconfigedit.exe a svctraceviewer.exe opravou rozmanitých problémy. Většina z nich byly drobných záležitostí, jako je název není definované nebo určité vzorce automatizace uživatelského rozhraní není implementovaná správně. Zatímco řada uživatelů nebude mít na paměti tyto nesprávné hodnoty, zákazníkům, kteří používají technologie pro usnadnění jako čtečky obrazovky zjistí tyto sady SDK nástroje přístup. Tyto opravy jistě, změnit některé předchozí chování, například pořadí fokus klávesnice. Aby bylo možné získat všechny opravy usnadnění v těchto nástrojů, můžete do souboru app.config následující:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Změna orientace|

