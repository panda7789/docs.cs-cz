### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Při odebírání položky z kolekce vlastní INCC havárií v selektoru

|   |   |
|---|---|
|Podrobnosti|<code>T:System.InvalidOperationException</code> Situace může nastat v následujícím scénáři:<ul><li>Položka ItemsSource pro <code>T:System.Windows.Controls.Primitives.Selector</code> je kolekce s vlastní implementaci <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>Vybraná položka je odebrána z kolekce.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Má <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (označující Neznámý pozice).</li></ul>Zásobník volání v výjimky začíná na System.Windows.Threading.Dispatcher.VerifyAccess() v System.Windows.DependencyObject.GetValue (Vlastnost DependencyProperty distribučního bodu) v System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject Element) této výjimce může dojít v rozhraní .net 4.5, pokud aplikace má více než jedno vlákno dispečera. V rozhraní .net 4.7 výjimka může dojít také v aplikacích s jedním vláknem dispečera. Je problém vyřešen v rozhraní .net 4.7.1.|
|Návrh|Upgrade na rozhraní .net 4.7.1.|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Modul runtime|

