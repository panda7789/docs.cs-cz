### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Vylepšení přístupnosti pro některé nástroje sady .NET SDK

|   |   |
|---|---|
|Podrobnosti|V SDK rozhraní .NET Framework 4.7.1 byly vylepšeny nástroje SvcConfigEditor.exe a SvcTraceViewer.exe opravou různých usnadnění. Většina z nich byly malé problémy, jako je název nedefinují nebo určité vzory pro automatizaci uživatelského rozhraní nebyl správně implementována. Při nesprávné hodnoty si nevšimnou mnoho uživatelů, zákazníci, kteří používají podpůrnou technologií, jako je čtečky obrazovky najdete tyto sady SDK nástroje přístupnější. Tyto opravy jistě, změňte některá předchozí chování, stejně jako pořadí fokus klávesnice. Zajistí všechno, co přístupnost opravy v těchto nástrojů můžete do souboru app.config následující:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Změna cílení|

