---
title: Novinky ve verzi 4.5 grafického subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 708b2fc231bfe7a9bc1f52872a0ec41c91931f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174703"
---
# <a name="whats-new-in-wpf-version-45"></a>Novinky ve verzi 4.5 grafického subsystému WPF
<a name="introduction"></a>Toto téma obsahuje informace o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nových a vylepšených funkcích ve verzi 4.5.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Ovládací prvek pásu karet](#ribbon_control)  
  
- [Vyšší výkon při zobrazování velkých sad seskupených dat](#grouped_virtualization)  
  
- [Nové funkce pro VirtualizingPanel](#VirtualizingPanel)  
  
- [Vazba na statické vlastnosti](#static_properties)  
  
- [Přístup k kolekcím v vláknech mimo uživatelské rozhraní](#xthread_access)  
  
- [Synchronně a asynchronně ověřování dat](#INotifyDataErrorInfo)  
  
- [Automatická aktualizace zdroje datové vazby](#delay)  
  
- [Vazba na typy, které implementují ICustomTypeProvider](#ICustomTypeProvider)  
  
- [Načítání informací o vazbě dat z výrazu vazby](#binding_state)  
  
- [Kontrola platného objektu DataContext](#DisconnectedSource)  
  
- [Změna umístění dat při změně hodnot dat (živé tvarování)](#live_shaping)  
  
- [Vylepšená podpora pro vytvoření slabého odkazu na událost](#weak_event_pattern)  
  
- [Nové metody pro třídu Dispečer](#async)  
  
- [Rozšíření značek pro události](#events_markup_extenions)  
  
<a name="ribbon_control"></a>
## <a name="ribbon-control"></a>Ovládací prvek pásu karet  
 WPF 4.5 je <xref:System.Windows.Controls.Ribbon.Ribbon> dodáván s ovládacím prvkem, který hostuje panel nástrojů rychlý přístup, nabídku aplikací a karty.  Další informace naleznete v tématu [Přehled pásu karet](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Vyšší výkon při zobrazování velkých sad seskupených dat  
 K virtualizaci uživatelského rozhraní dochází, když jsou podmnožina prvků uživatelského rozhraní (UI) generována z většího počtu datových položek na základě toho, které položky jsou viditelné na obrazovce. Definuje <xref:System.Windows.Controls.VirtualizingPanel> připojenou <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> vlastnost, která umožňuje virtualizaci ui pro seskupená data.  Další informace o seskupování dat najdete v tématu Postup: Řazení a seskupování dat pomocí zobrazení v XAML.  Další informace o virtualizaci seskupených <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dat naleznete v připojené vlastnosti.  
  
<a name="VirtualizingPanel"></a>
## <a name="new-features-for-the-virtualizingpanel"></a>Nové funkce pro VirtualizingPanel  
  
1. Pomocí <xref:System.Windows.Controls.VirtualizingPanel> <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> připojené vlastnosti <xref:System.Windows.Controls.VirtualizingStackPanel>můžete určit, zda například například zobrazí částečné položky. Pokud <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> je <xref:System.Windows.Controls.ScrollUnit.Item>nastavena <xref:System.Windows.Controls.VirtualizingPanel> na , bude zobrazovat pouze položky, které jsou zcela viditelné. Pokud <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> je <xref:System.Windows.Controls.ScrollUnit.Pixel>nastavena <xref:System.Windows.Controls.VirtualizingPanel> na , může zobrazit částečně viditelné položky.  
  
2. Můžete určit velikost mezipaměti před a za výřezem, <xref:System.Windows.Controls.VirtualizingPanel> když <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> je virtualizace pomocí připojené vlastnosti.  Mezipaměť je velikost místa nad nebo pod výřezem, ve kterém nejsou položky virtualizovány.  Použití mezipaměti, aby se zabránilo generování prvků uživatelského rozhraní při jejich posouvání do zobrazení může zlepšit výkon. Mezipaměť je naplněna s nižší prioritou, takže aplikace během operace nepřestane reagovat. Vlastnost <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> určuje měrnou jednotku, která <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>je používána .  
  
<a name="static_properties"></a>
## <a name="binding-to-static-properties"></a>Vazba na statické vlastnosti  
 Statické vlastnosti můžete použít jako zdroj datové vazby. Modul datové vazby rozpozná, když se změní hodnota vlastnosti, pokud je vyvolána statická událost.  Například pokud třída `SomeClass` definuje statickou `MyProperty`vlastnost `SomeClass` s názvem , můžete definovat statickou událost, která je vyvolána při změně hodnoty. `MyProperty`  Statická událost může použít některý z následujících podpisů.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Všimněte si, že v prvním případě třída zpřístupňuje <xref:System.EventArgs> statickou událost s názvem *PropertyName,* `Changed` která předá obslužné rutině události.  V druhém případě třída zpřístupňuje statickou událost s názvem, `StaticPropertyChanged` která předá <xref:System.ComponentModel.PropertyChangedEventArgs> obslužné rutině události. Třída, která implementuje statickou vlastnost, můžete zvýšit oznámení o změně vlastnosti pomocí obou metod.  
  
<a name="xthread_access"></a>
## <a name="accessing-collections-on-non-ui-threads"></a>Přístup k kolekcím v vláknech mimo uživatelské rozhraní  
 WPF umožňuje přístup a upravit kolekce dat na vláknech než ten, který vytvořil kolekci.  To umožňuje použít vlákno na pozadí pro příjem dat z externího zdroje, jako je například databáze, a zobrazení dat ve vlákně uživatelského rozhraní.  Pomocí jiného vlákna upravit kolekci, uživatelské rozhraní zůstává reagovat na interakci uživatele.  
  
<a name="INotifyDataErrorInfo"></a>
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchronně a asynchronně ověřování dat  
 Rozhraní <xref:System.ComponentModel.INotifyDataErrorInfo> umožňuje třídy datových entit implementovat vlastní ověřovací pravidla a vystavit výsledky ověření asynchronně. Toto rozhraní také podporuje vlastní objekty chyb, více chyb na vlastnost, chyby mezi vlastnostmi a chyby na úrovni entity.  Další informace naleznete v tématu <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automatická aktualizace zdroje datové vazby  
 Pokud použijete datovou vazbu k aktualizaci <xref:System.Windows.Data.BindingBase.Delay%2A> zdroje dat, můžete pomocí vlastnosti určit dobu, která má uplynout po změně vlastnosti v cíli před aktualizací zdroje.  Předpokládejme například, že <xref:System.Windows.Controls.Slider> máte, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> která má data vlastnosti obousměrně vázána <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> na vlastnost <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>datového objektu a vlastnost je nastavena na .  V tomto příkladu, když <xref:System.Windows.Controls.Slider>uživatel přesune , zdroj <xref:System.Windows.Controls.Slider> aktualizuje pro každý obrazový bod, který přesune.  Zdrojový objekt obvykle potřebuje hodnotu jezdce pouze v případě, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> že se jezdec přestane měnit.  Chcete-li zabránit aktualizaci <xref:System.Windows.Data.BindingBase.Delay%2A> zdroje příliš často, použijte k určení, že zdroj by neměl být aktualizován, dokud neuplyne určitá doba po zastavení pohybu palce.  
  
<a name="ICustomTypeProvider"></a>
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Vazba na typy, které implementují ICustomTypeProvider  
 WPF podporuje datové vazby <xref:System.Reflection.ICustomTypeProvider>na objekty, které implementují , označované také jako vlastní typy.  Vlastní typy můžete použít v následujících případech.  
  
1. Jako <xref:System.Windows.PropertyPath> v datové vazbě. Například <xref:System.Windows.Data.Binding.Path%2A> vlastnost <xref:System.Windows.Data.Binding> může odkazovat na vlastnost vlastního typu.  
  
2. Jako hodnota vlastnosti. <xref:System.Windows.DataTemplate.DataType%2A>  
  
3. Jako typ, který určuje automaticky generované <xref:System.Windows.Controls.DataGrid>sloupce v .  
  
<a name="binding_state"></a>
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Načítání informací o vazbě dat z výrazu vazby  
 V některých případech můžete <xref:System.Windows.Data.BindingExpression> získat <xref:System.Windows.Data.Binding> a potřebujete informace o zdrojové a cílové objekty vazby.  Byla přidána nová api, která umožňují získat zdrojový nebo cílový objekt nebo přidruženou vlastnost.  Pokud máte <xref:System.Windows.Data.BindingExpression>, použijte následující api získat informace o cíli a zdroji.  
  
|Chcete-li najít tuto hodnotu vazby|Použít toto rozhraní API|  
|---------------------------------------|------------------|  
|Cílový objekt|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Cílová vlastnost|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Zdrojový objekt|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Zdrojová vlastnost|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Zda <xref:System.Windows.Data.BindingExpression> patří do<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Majitel<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>
## <a name="checking-for-a-valid-datacontext-object"></a>Kontrola platného objektu DataContext  
 Existují případy, <xref:System.Windows.FrameworkElement.DataContext%2A> kdy kontejner položky <xref:System.Windows.Controls.ItemsControl> v stane odpojen.  Kontejner položky je prvek ui, který <xref:System.Windows.Controls.ItemsControl>zobrazuje položku v .  Pokud <xref:System.Windows.Controls.ItemsControl> je data vázána na kolekci, kontejner položky je generován pro každou položku. V některých případech jsou kontejnery položek odebrány z vizuálního stromu. Dva typické případy, kdy je odebrán kontejner položky jsou při odebrání položky <xref:System.Windows.Controls.ItemsControl>z podkladové kolekce a při virtualizaci je povolena na . V těchto případech <xref:System.Windows.FrameworkElement.DataContext%2A> bude vlastnost kontejneru položky nastavena na sentinel <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> objekt, který je vrácen statickou vlastností.  Měli byste zkontrolovat, <xref:System.Windows.FrameworkElement.DataContext%2A> zda <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> se rovná objektu před přístupem <xref:System.Windows.FrameworkElement.DataContext%2A> kontejneru položky.  
  
<a name="live_shaping"></a>
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Změna umístění dat při změně hodnot dat (živé tvarování)  
 Kolekci dat lze seskupit, seřadit nebo filtrovat. WPF 4.5 umožňuje data, která mají být uspořádány při změně dat. Předpokládejme například, že <xref:System.Windows.Controls.DataGrid> aplikace používá k vypsat zásoby na akciovém trhu a zásoby jsou seřazeny podle hodnoty akcií. Pokud je u akcií povoleno <xref:System.Windows.Data.CollectionView>živé třídění , pozice <xref:System.Windows.Controls.DataGrid> akcie v pohybech, když se hodnota akcie stane větší nebo menší než hodnota jiné akcie.   Další informace naleznete <xref:System.ComponentModel.ICollectionViewLiveShaping> v rozhraní.  
  
<a name="weak_event_pattern"></a>
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Vylepšená podpora pro vytvoření slabého odkazu na událost  
 Implementace vzor slabé události je nyní jednodušší, protože odběratelé událostí se mohou zúčastnit bez implementace další rozhraní.  Obecná <xref:System.Windows.WeakEventManager> třída také umožňuje předplatitelům účastnit se slabé <xref:System.Windows.WeakEventManager> události vzor, pokud vyhrazené neexistuje pro určitou událost.  Další informace naleznete [v tématu Slabé vzory událostí](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>
## <a name="new-methods-for-the-dispatcher-class"></a>Nové metody pro třídu Dispečer  
 Třída Dispečer definuje nové metody pro synchronní a asynchronní operace.  Synchronní <xref:System.Windows.Threading.Dispatcher.Invoke%2A> metoda definuje přetížení, které <xref:System.Action> trvat nebo <xref:System.Func%601> parametr. Nová asynchronní metoda <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, také <xref:System.Action> přebírá <xref:System.Func%601> nebo jako parametr zpětného volání a vrátí hodnotu a <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>.   A <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601> třídy <xref:System.Threading.Tasks.Task> definují vlastnost.  Při volání <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>můžete `await` klíčové slovo použít <xref:System.Windows.Threading.DispatcherOperation> s přidruženým nebo přidruženým <xref:System.Threading.Tasks.Task>. Pokud potřebujete čekat synchronně pro <xref:System.Threading.Tasks.Task> který je <xref:System.Windows.Threading.DispatcherOperation> vrácena <xref:System.Windows.Threading.DispatcherOperation%601>nebo <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> , volání metody rozšíření. Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> bude mít za následek zablokování, pokud je operace zařazena do fronty v volajícím vlákně. Další informace o <xref:System.Threading.Tasks.Task> použití asynchronní operace naleznete v [tématu Task Parallelism (Task Parallel library).](../../../standard/parallel-programming/task-based-asynchronous-programming.md)  
  
<a name="events_markup_extenions"></a>
## <a name="markup-extensions-for-events"></a>Rozšíření značek pro události  
 WPF 4.5 podporuje značkovací rozšíření pro události.  Zatímco WPF nedefinuje rozšíření značek, které se má použít pro události, třetí strany jsou schopny vytvořit rozšíření značek, které lze použít s událostmi.  
  
## <a name="see-also"></a>Viz také

- [Co je nového v rozhraní .NET Framework](../../whats-new/index.md)
