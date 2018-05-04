### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>Výběr textu položka textového pole nebo PasswordBox WPF neodpovídá pravidlům systému barvy

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a starší verze, WPF <code>System.Windows.Controls.TextBox</code> a <code>System.Windows.Controls.PasswordBox</code> může mít pouze výběr textu v Adorner vrstvě. V některých motivy systému to by occlude textu, takže těžko čitelný.  V rozhraní .NET Framework 4.7.2 a novější, vývojáři mají možnost povolení výběru nezaložené Adorner vykreslování schéma, které řeší tento problém.|
|Návrh|Vývojáři, který chce využívat tuto změnu musí nastavit příznak následující AppContext správně.  Abyste mohli tuto funkci využívat, musí být nainstalovaná verze rozhraní .NET Framework 4.7.2 nebo vyšší. Povolit výběr nezaložené adorner, použijte následující AppContext příznak.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Změna orientace|

