### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Fokus klávesnice nyní správně přesune ve více vrstvách hostování WinForms nebo WPF

|   |   |
|---|---|
|Podrobnosti|Vezměte v úvahu aplikace WPF hostování ovládací prvek WinForms, který je zase hostitelem ovládacích prvků WPF. Uživatelé se možná nebudou moct kartu z vrstvy WinForms, pokud je první nebo poslední ovládací prvek v této vrstvě WPF <code>System.Windows.Forms.Integration.ElementHost</code>. Tato změna řeší tento problém, a uživatelé mají nyní možnost kartu z vrstvy WinForms. Automatizované aplikace, které spoléhají na fokus nikdy uvození vrstvě WinForms už nemusí fungovat podle očekávání.|
|Návrh|Jako vývojář, který chce využít tato změna při cílení na určitou verzi rozhraní framework níže .NET 4.7.2 můžete nastavit následující sadu příznaků AppContext na hodnotu false pro změnu, aby byla povolená.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikace WPF, musíte vyjádřit výslovný souhlas s všechny dřívější vylepšení přístupnosti získat novější vylepšení. Jinými slovy, i <code>Switch.UseLegacyAccessibilityFeatures</code> a <code>Switch.UseLegacyAccessibilityFeatures.2</code> přepínače musí být setA vývojář, který vyžaduje funkci předchozí zároveň cílí na .NET 4.7.2 nebo větší může nastavit následující AppContext příznak na hodnotu true, tato změna se deaktivuje.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Mění se cílení|

