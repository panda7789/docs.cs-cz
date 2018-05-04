### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Fokus klávesnice nyní správně přesune napříč více vrstev hostování WinForms/WPF

|   |   |
|---|---|
|Podrobnosti|Vezměte v úvahu aplikace WPF hostování ovládacího prvku WinForms, který naopak hostuje ovládacích prvků WPF. Uživatelé nemusí být schopni kartě mimo WinForms vrstvy, pokud je první nebo poslední ovládací prvek v této vrstvě WPF <code>System.Windows.Forms.Integration.ElementHost</code>. Tato změna řeší tento problém a uživatelé mohou nyní na kartě mimo vrstvě WinForms. Automatizované aplikace, které závisí na fokus nikdy uvozovací znaky vrstvě WinForms může přestane fungovat podle očekávání.|
|Návrh|Vývojáři, který chce využívat tuto změnu při cílení na verzi framework pod .NET 4.7.2 můžete nastavit následující sadu AppContext příznaky na hodnotu false pro změna, která má být povolena.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikace WPF musí vyjádřit výslovný souhlas pro všechny časná vylepšení přístupnosti získat novější vylepšení. Jinými slovy, jak <code>Switch.UseLegacyAccessibilityFeatures</code> a <code>Switch.UseLegacyAccessibilityFeatures.2</code> přepínače musí být setA vývojáři, který vyžaduje předchozí funkce při cílení na rozhraní .NET 4.7.2 nebo větší může nastavit příznak následující AppContext na hodnotu true pro změna, která má být zakázáno.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Změna orientace|

