---
title: Novinky ve verzi 4.5 grafického subsystému WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 03f785da018cacdec643fa196bdd0c6d5d7c7f70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325823"
---
# <a name="whats-new-in-wpf-version-45"></a>Novinky ve verzi 4.5 grafického subsystému WPF
<a name="introduction"></a> Toto téma obsahuje informace o nových a vylepšených funkcích [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] verze 4.5.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Ovládací prvek pásu karet](#ribbon_control)  
  
-   [Vylepšili jsme výkon při zobrazování velkých sad seskupených dat](#grouped_virtualization)  
  
-   [Nové funkce pro VirtualizingPanel](#VirtualizingPanel)  
  
-   [Vytvoření vazby na statické vlastnosti](#static_properties)  
  
-   [Přístupem ke kolekcím v uživatelském rozhraní vláken](#xthread_access)  
  
-   [Synchronní a asynchronní ověření dat.](#INotifyDataErrorInfo)  
  
-   [Automatické aktualizace zdrojové datové vazby](#delay)  
  
-   [Vytvoření vazby na typy ICustomTypeProvider této implementace](#ICustomTypeProvider)  
  
-   [Načítání informací o vázání dat z vazbového výrazu](#binding_state)  
  
-   [Kontrolují se platný objekt kontextu DataContext](#DisconnectedSource)  
  
-   [Přemístění dat při změně dat hodnot (živé tvarování)](#live_shaping)  
  
-   [Vylepšená podpora pro stanovení Slabý odkaz na událost](#weak_event_pattern)  
  
-   [Nové metody pro třídu dispečer](#async)  
  
-   [Rozšíření značek pro události](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Ovládací prvek pásu karet  
 WPF 4.5 je součástí <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvek, který je hostitelem panelu nástrojů Rychlý přístup, nabídky aplikace a karet.  Další informace najdete v tématu [přehled pásu karet](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Vylepšili jsme výkon při zobrazování velkých sad seskupených dat  
 Virtualizace uživatelského rozhraní nastane, pokud se část uživatelského rozhraní (UI) jsou generovány elementy z větší počet datových položek podle položky, které jsou viditelné na obrazovce. <xref:System.Windows.Controls.VirtualizingPanel> Definuje <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> přidružená vlastnost, která umožňuje virtualizace uživatelského rozhraní pro seskupené data.  Další informace o seskupování dat, naleznete v tématu Postupy: Řazení a seskupení dat použitím zobrazení XAML.  Další informace o virtualizaci seskupená data, najdete v článku <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> přidružená vlastnost.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nové funkce pro VirtualizingPanel  
  
1. Můžete určit, jestli <xref:System.Windows.Controls.VirtualizingPanel>, například <xref:System.Windows.Controls.VirtualizingStackPanel>, zobrazí částečných položek pomocí <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> přidružená vlastnost. Pokud <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> je nastavena na <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> zobrazí pouze položky, které jsou zcela viditelné. Pokud <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> je nastavena na <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> částečně viditelné položky lze zobrazit.  
  
2. Můžete zadat velikost mezipaměti před a po zobrazení při <xref:System.Windows.Controls.VirtualizingPanel> virtualizace pomocí <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> přidružená vlastnost.  Mezipaměť je množství místa nad nebo pod zobrazení, ve kterém nejsou virtualizovány položek.  Použití mezipaměti pro zabránění generování prvků uživatelského rozhraní, jako jste přešli do zobrazení může zlepšit výkon. Tak, aby aplikace není přestane během operace se mezipaměť naplní s nižší prioritou. <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Vlastnost určuje, který používá měrné jednotky <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Vytvoření vazby na statické vlastnosti  
 Statické vlastnosti můžete použít jako zdroj datové vazby. Modul vazby dat rozpozná při změně hodnoty vlastnosti Pokud statické událost se vyvolá.  Například pokud třída `SomeClass` definuje statickou vlastnost s názvem `MyProperty`, `SomeClass` můžete definovat statické události, která se vyvolá se, když hodnota `MyProperty` změny.  Statické události můžete použít kteroukoli z následující signatury.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Všimněte si, že v prvním případě zpřístupní třídu statické událost s názvem *PropertyName* `Changed` , který předá <xref:System.EventArgs> obslužné rutiny události.  V druhém případě třída zveřejňuje statické událost s názvem `StaticPropertyChanged` , který předá <xref:System.ComponentModel.PropertyChangedEventArgs> obslužné rutiny události. Třídu, která implementuje statickou vlastnost můžete zvolit vytváření vlastnost – oznámení o změnách pomocí některé z metod.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Přístupem ke kolekcím v uživatelském rozhraní vláken  
 WPF umožňuje přístup a úpravy dat kolekce na vláknech než ten, který vytvoří kolekci.  To umožňuje použití vlákna na pozadí pro příjem dat z externího zdroje, jako je například databáze a zobrazení dat na vlákně UI.  S použitím jiného vlákna k úpravě kolekce, uživatelské rozhraní stále poměrně rychle reaguje na interakci uživatele.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchronní a asynchronní ověření dat.  
 <xref:System.ComponentModel.INotifyDataErrorInfo> Rozhraní umožňuje datové entity třídy k implementaci vlastních ověřovacích pravidel a zpřístupňují výsledky ověření asynchronně. Toto rozhraní podporuje také objekty vlastní chyby, více chyb na vlastnost, různé vlastnosti chyb a chyb na úrovni entity.  Další informace naleznete v tématu <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automatické aktualizace zdrojové datové vazby  
 Pokud používáte datové vazby k aktualizaci zdroje dat, můžete použít <xref:System.Windows.Data.BindingBase.Delay%2A> vlastnosti a určit dobu, jakou předat po změně vlastnosti na cíli před aktualizací zdroje.  Předpokládejme například, že máte <xref:System.Windows.Controls.Slider> , který má jeho <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> data vlastnosti obousměrný svázanou s vlastností datového objektu a <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> je nastavena na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  V tomto příkladu, když uživatel přesune <xref:System.Windows.Controls.Slider>, zdroj aktualizace pro každý pixel, který <xref:System.Windows.Controls.Slider> přesouvá.  Zdrojový objekt obvykle musí hodnota posuvníku pouze tehdy, když posuvníku <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zastaví změna.  Chcete-li zabránit, aktualizaci zdroje příliš často, použijte <xref:System.Windows.Data.BindingBase.Delay%2A> zadat zdroj by neměly být aktualizovány, až uplyne množství času po jezdce zastaví přesunutí.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Vytvoření vazby na typy ICustomTypeProvider této implementace  
 WPF podporuje datovou vazbu pro objekty, které implementují <xref:System.Reflection.ICustomTypeProvider>, označovaný také jako vlastní typy.  V následujících případech můžete použít vlastní typy.  
  
1. Jako <xref:System.Windows.PropertyPath> v datové vazbě. Například <xref:System.Windows.Data.Binding.Path%2A> vlastnost <xref:System.Windows.Data.Binding> může odkazovat na vlastnost vlastního typu.  
  
2. Jako hodnotu <xref:System.Windows.DataTemplate.DataType%2A> vlastnost.  
  
3. Jako typ, který určuje automaticky generované sloupce v <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Načítání informací o vázání dat z vazbového výrazu  
 V některých případech se mohou zobrazovat <xref:System.Windows.Data.BindingExpression> z <xref:System.Windows.Data.Binding> a potřebujete informace o zdrojové a cílové objektů vazby.  Přibyla nová rozhraní API vám umožní získat zdrojové nebo cílové objektů nebo přidružené vlastnosti.  Pokud máte <xref:System.Windows.Data.BindingExpression>, použijte následující rozhraní API a získat informace o zdrojové a cílové.  
  
|Tuto hodnotu najdete vazby|Pomocí tohoto rozhraní API|  
|---------------------------------------|------------------|  
|Cílový objekt|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Vlastnost target|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Zdrojový objekt|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Vlastnost source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Zda <xref:System.Windows.Data.BindingExpression> patří do <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Vlastníka <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Kontrolují se platný objekt kontextu DataContext  
 Existují případy, kdy <xref:System.Windows.FrameworkElement.DataContext%2A> položky kontejneru v <xref:System.Windows.Controls.ItemsControl> se odpojí.  Kontejner položek je prvek uživatelského rozhraní, které zobrazuje položky v <xref:System.Windows.Controls.ItemsControl>.  Když <xref:System.Windows.Controls.ItemsControl> data vazbou na určitou kolekci, kontejner položek se generuje pro každou položku. V některých případech kontejnery položky budou odebrány z vizuálního stromu. Jsou dva typické případy, ve kterém je kontejner položek odebrána po odebrání položky ze zdrojové kolekce a když je povolena virtualizace na <xref:System.Windows.Controls.ItemsControl>. V těchto případech <xref:System.Windows.FrameworkElement.DataContext%2A> nastavíte vlastnost kontejner položek sentinel objekt, který je vrácený <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> statickou vlastnost.  Byste měli zkontrolovat, zda <xref:System.Windows.FrameworkElement.DataContext%2A> rovná <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> objektu před přístupem k <xref:System.Windows.FrameworkElement.DataContext%2A> položky kontejneru.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Přemístění dat při změně dat hodnot (živé tvarování)  
 Shromažďování dat můžete seskupené, řazení nebo filtrovat. WPF 4.5 umožňuje data, která mají být změnit jejich uspořádání, když se změní data. Předpokládejme například, že aplikace používá <xref:System.Windows.Controls.DataGrid> na seznamu v burzovního trhu a populací jsou seřazeny podle uložené hodnoty. Pokud řazení za provozu je zapnutá zásob <xref:System.Windows.Data.CollectionView>, pozice skladě v <xref:System.Windows.Controls.DataGrid> přesune, když se stane hodnota stock větší nebo menší než jiný akcie hodnotu.   Další informace najdete v tématu <xref:System.ComponentModel.ICollectionViewLiveShaping> rozhraní.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Vylepšená podpora pro stanovení Slabý odkaz na událost  
 Implementace vzoru slabých událostí je teď jednodušší, protože Odběratelé událostí mohl podílet na to bez implementace rozhraní navíc.  Obecné <xref:System.Windows.WeakEventManager> tříd také umožňuje předplatitelům se účastnit slabý vzor událostí, je-li to vyhrazené <xref:System.Windows.WeakEventManager> pro určitou událost neexistuje.  Další informace najdete v tématu [slabé vzory událostí](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nové metody pro třídu dispečer  
 Dispečer třída definuje nové metody pro synchronní a asynchronní operace.  Synchronní <xref:System.Windows.Threading.Dispatcher.Invoke%2A> přetížení, která přijímají definuje metody <xref:System.Action> nebo <xref:System.Func%601> parametru. Nový asynchronní metody <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, využívá taky <xref:System.Action> nebo <xref:System.Func%601> jako parametru zpětného volání a vrátí <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>.   <xref:System.Windows.Threading.DispatcherOperation> a <xref:System.Windows.Threading.DispatcherOperation%601> třídy definují <xref:System.Threading.Tasks.Task> vlastnost.  Při volání <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, můžete použít `await` – klíčové slovo se buď <xref:System.Windows.Threading.DispatcherOperation> nebo přidružené <xref:System.Threading.Tasks.Task>. Pokud budete muset počkat synchronně <xref:System.Threading.Tasks.Task> , který je vrácen <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, volání <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> – metoda rozšíření. Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> způsobí zablokování, pokud operace je zařazeno do fronty v volajícího vlákna. Další informace o používání <xref:System.Threading.Tasks.Task> provádět asynchronní operace, najdete v článku [funkční paralelismus (Task Parallel Library)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Rozšíření značek pro události  
 WPF 4.5 podporuje – rozšíření značek pro události.  Zatímco WPF nedefinuje rozšíření značek, který má být použit pro události, budou moct vytvořit rozšíření značek, který lze použít s událostmi třetím stranám.  
  
## <a name="see-also"></a>Viz také:

- [Novinky v rozhraní .NET Framework](../../whats-new/index.md)
