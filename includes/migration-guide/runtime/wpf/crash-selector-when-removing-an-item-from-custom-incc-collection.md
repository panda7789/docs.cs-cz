### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Při odebrání položky z vlastní kolekce INCC k chybě v oblasti pro výběr

|   |   |
|---|---|
|Podrobnosti|<code>T:System.InvalidOperationException</code> Může dojít v následujících situacích:<ul><li>Vlastnost ItemsSource pro <code>T:System.Windows.Controls.Primitives.Selector</code> je kolekce s vlastní implementace <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>Vybraná položka je odebrán z kolekce.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Má <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (značí, že neznámé místo).</li></ul>Zásobník volání výjimky začíná System.Windows.Threading.Dispatcher.VerifyAccess() na na System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject System.Windows.DependencyObject.GetValue (Vlastnost DependencyProperty distribučního bodu) Element) této výjimce může dojít v rozhraní .NET Framework 4.5, pokud má aplikace více než jedno vlákno dispečera. V rozhraní .NET Framework 4.7 výjimky může vzniknout také v aplikacích s jedním vláknem a Dispečerem. Problém je vyřešen v rozhraní .NET Framework 4.7.1.|
|Návrh|Upgrade na rozhraní .NET Framework 4.7.1.|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Modul runtime|

