### <a name="wpf-pointer-based-touch-stack"></a>WPF Touch na základě ukazatel zásobníku

|   |   |
|---|---|
|Podrobnosti|Tato změna přidá možnost povolit volitelné WM_POINTER na základě WPF touch/pera zásobníku.  Vývojáři, kteří nepovolujte explicitně to měli vidět žádná změna v chování touch/pera WPF. Aktuální známé problémy s volitelné WM_POINTER na základě touch/pera zásobníku:<ul><li>Žádné podporou kreslení v reálném čase.</li><li>Při rukopisu a StylusPlugins budou i nadále fungovat, zpracovávají na vlákna uživatelského rozhraní, což může vést k nižšímu výkonu.</li><li>Chování změny z důvodu změn v povýšení z událostí touch/pera na události myši</li><li>Manipulace s může chovat jinak</li><li>Přetažením nezobrazí odpovídající zpětnou vazbu pro dotykové ovládání</li><li>To nemá vliv na vstup pera</li><li>Přetažením lze inicializovat už na událostí touch/pera</li><li>To potenciálně může na aplikace, dokud je zjištěna vstup z myši.</li><li>Místo toho by vývojáři Zahájit přetažení a vyřadit z událostí myši.</li></ul>|
|Návrh|Vývojáři, kteří chtějí povolit tento zásobník můžete přidat či sloučení následujícího souboru App.config jejich aplikace:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Odebrání to nebo nastavení na hodnotu false se vypne této volitelné zásobníku. Všimněte si, že tento zásobník je k dispozici pouze při aktualizaci Creators Windows 10 a vyšší.|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna orientace|

