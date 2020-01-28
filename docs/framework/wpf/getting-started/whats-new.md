---
title: Novinky ve verzi 4.5 grafického subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 8eff8da7746047c450b2e23af63d43b13f3b970c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746929"
---
# <a name="whats-new-in-wpf-version-45"></a>Novinky ve verzi 4.5 grafického subsystému WPF
<a name="introduction"></a>Toto téma obsahuje informace o nových a vylepšených funkcích v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] verze 4,5.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Ovládací prvek pásu karet](#ribbon_control)  
  
- [Vylepšený výkon při zobrazování velkých sad seskupených dat](#grouped_virtualization)  
  
- [Nové funkce pro VirtualizingPanel](#VirtualizingPanel)  
  
- [Vazba na statické vlastnosti](#static_properties)  
  
- [Přístup ke kolekcím na vláknech bez uživatelského rozhraní](#xthread_access)  
  
- [Synchronní a asynchronní ověřování dat](#INotifyDataErrorInfo)  
  
- [Automatická aktualizace zdroje datové vazby](#delay)  
  
- [Vazba na typy, které implementují ICustomTypeProvider](#ICustomTypeProvider)  
  
- [Načítání informací o vazbách dat z výrazu vazby](#binding_state)  
  
- [Kontroluje se platný objekt DataContext.](#DisconnectedSource)  
  
- [Změna umístění dat při změně hodnot dat (živé tvarování)](#live_shaping)  
  
- [Vylepšená podpora pro navázání slabého odkazu na událost](#weak_event_pattern)  
  
- [Nové metody pro třídu Dispatcher](#async)  
  
- [Rozšíření značek pro události](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Ovládací prvek pásu karet  
 WPF 4,5 se dodává s ovládacím prvkem <xref:System.Windows.Controls.Ribbon.Ribbon>, který je hostitelem panelu nástrojů Rychlý přístup, nabídky aplikace a karet.  Další informace najdete v [přehledu pásu karet](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Vylepšený výkon při zobrazování velkých sad seskupených dat  
 K virtualizaci uživatelského rozhraní dojde v případě, že je vygenerována podmnožina prvků uživatelského rozhraní (UI) z většího počtu datových položek na základě toho, které položky jsou na obrazovce viditelné. <xref:System.Windows.Controls.VirtualizingPanel> definuje vlastnost připojenou <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A>, která umožňuje virtualizaci uživatelského rozhraní pro seskupená data.  Další informace o seskupování dat najdete v tématu Postupy: řazení a seskupování dat pomocí zobrazení v jazyce XAML.  Další informace o virtualizaci seskupených dat najdete v <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> vlastnosti připojené.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nové funkce pro VirtualizingPanel  
  
1. Můžete určit, zda <xref:System.Windows.Controls.VirtualizingPanel>, například <xref:System.Windows.Controls.VirtualizingStackPanel>, zobrazuje částečné položky pomocí <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> připojená vlastnost. Pokud je <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> nastaveno na <xref:System.Windows.Controls.ScrollUnit.Item>, bude <xref:System.Windows.Controls.VirtualizingPanel> zobrazovat pouze položky, které jsou zcela viditelné. Pokud je <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> nastaveno na <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> může zobrazit částečně viditelné položky.  
  
2. Velikost mezipaměti můžete zadat před a po zobrazení, když je <xref:System.Windows.Controls.VirtualizingPanel> virtualizovat pomocí vlastnosti <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> připojené.  Mezipaměť je množství místa nad nebo pod zobrazením, ve kterém položky nejsou virtualizované.  Použití mezipaměti, aby nedocházelo k vygenerování prvků uživatelského rozhraní, když se posouvají do zobrazení, může zvýšit výkon. Mezipaměť je naplněna s nižší prioritou, takže aplikace během operace přestane reagovat. Vlastnost <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Určuje jednotku měření, kterou používá <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Vazba na statické vlastnosti  
 Jako zdroj datové vazby můžete použít statické vlastnosti. Modul vazby dat rozpoznává při změně hodnoty vlastnosti, pokud je vyvolána statická událost.  Například pokud třída `SomeClass` definuje statickou vlastnost nazvanou `MyProperty`, `SomeClass` může definovat statickou událost, která je vyvolána, když se změní hodnota `MyProperty`.  Statická událost může použít kteroukoli z následujících signatur.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Všimněte si, že v prvním případě třída zveřejňuje statickou událost s názvem *PropertyName*`Changed`, která předává <xref:System.EventArgs> obslužné rutině události.  Ve druhém případě třída zveřejňuje statickou událost s názvem `StaticPropertyChanged`, která předává <xref:System.ComponentModel.PropertyChangedEventArgs> obslužné rutině události. Třída, která implementuje statickou vlastnost, se může rozhodnout pro vyvolání oznámení o změně vlastnosti pomocí obou metod.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Přístup ke kolekcím na vláknech bez uživatelského rozhraní  
 WPF umožňuje přístup ke kolekcím dat a jejich úpravy v jiných vláknech, než je ta, která kolekci vytvořila.  To umožňuje použít vlákno na pozadí pro příjem dat z externího zdroje, jako je například databáze, a zobrazit data ve vlákně uživatelského rozhraní.  Když použijete jiné vlákno pro úpravu kolekce, vaše uživatelské rozhraní zůstává reagovat na interakci s uživatelem.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchronní a asynchronní ověřování dat  
 Rozhraní <xref:System.ComponentModel.INotifyDataErrorInfo> umožňuje třídám datových entit implementovat vlastní ověřovací pravidla a asynchronně zobrazit výsledky ověřování. Toto rozhraní také podporuje vlastní chybové objekty, více chyb na vlastnost, chyby křížových vlastností a chyby na úrovni entit.  Další informace najdete v tématu <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automatická aktualizace zdroje datové vazby  
 Použijete-li datovou vazbu k aktualizaci zdroje dat, můžete použít vlastnost <xref:System.Windows.Data.BindingBase.Delay%2A> k určení množství času, které se má předat po změně vlastnosti v cíli před zdrojovými aktualizacemi.  Předpokládejme například, že máte <xref:System.Windows.Controls.Slider>, který má svůj <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastností dat, který má obousměrný vazbu na vlastnost datového objektu a vlastnost <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> je nastavena na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  V tomto příkladu když uživatel přesune <xref:System.Windows.Controls.Slider>, aktualizuje se zdroj pro každý pixel, který <xref:System.Windows.Controls.Slider> přesune.  Zdrojový objekt obvykle potřebuje hodnotu posuvníku pouze v případě, že se <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> posuvníku přestane měnit.  Chcete-li zabránit tomu, aby byl zdroj příliš často aktualizován, použijte <xref:System.Windows.Data.BindingBase.Delay%2A> k určení, že zdroj by neměl být aktualizován, dokud neuplyne určitý časový interval, po kterém se pohyb zastaví.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Vazba na typy, které implementují ICustomTypeProvider  
 WPF podporuje datovou vazbu na objekty, které implementují <xref:System.Reflection.ICustomTypeProvider>, označované také jako vlastní typy.  V následujících případech můžete použít vlastní typy.  
  
1. Jako <xref:System.Windows.PropertyPath> v datové vazbě. Například vlastnost <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding> může odkazovat na vlastnost vlastního typu.  
  
2. Jako hodnotu vlastnosti <xref:System.Windows.DataTemplate.DataType%2A>.  
  
3. Jako typ, který určuje automaticky generované sloupce v <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Načítání informací o vazbách dat z výrazu vazby  
 V některých případech můžete získat <xref:System.Windows.Data.BindingExpression> <xref:System.Windows.Data.Binding> a potřebujete informace o zdrojovém a cílovém objektu vazby.  Přidala se nová rozhraní API, která vám umožní získat zdrojový nebo cílový objekt nebo přidruženou vlastnost.  Pokud máte <xref:System.Windows.Data.BindingExpression>, použijte následující rozhraní API k získání informací o cíli a zdroji.  
  
|Vyhledání této hodnoty vazby|Použít toto rozhraní API|  
|---------------------------------------|------------------|  
|Cílový objekt|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Vlastnost target|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Zdrojový objekt|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Vlastnost source|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Zda <xref:System.Windows.Data.BindingExpression> patří do <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Vlastník <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Kontroluje se platný objekt DataContext.  
 Existují případy, kdy se odpojí <xref:System.Windows.FrameworkElement.DataContext%2A> kontejneru položek v <xref:System.Windows.Controls.ItemsControl>.  Kontejner položek je prvek uživatelského rozhraní, který zobrazuje položku v <xref:System.Windows.Controls.ItemsControl>.  Pokud je <xref:System.Windows.Controls.ItemsControl> dat vázaných na kolekci, je pro každou položku vygenerován kontejner položek. V některých případech jsou kontejnery položek odebrány z vizuálního stromu. Pokud je odebrána položka ze základní kolekce a když je na <xref:System.Windows.Controls.ItemsControl>povolena virtualizace, jsou dva typické případy, kdy je odebrán kontejner položek. V těchto případech bude vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> kontejneru položek nastavena na objekt Sentinel, který je vrácen vlastností static <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType>.  Před přístupem k <xref:System.Windows.FrameworkElement.DataContext%2A> kontejneru položky byste měli ověřit, zda je <xref:System.Windows.FrameworkElement.DataContext%2A> rovna <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> objektu.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Změna umístění dat při změně hodnot dat (živé tvarování)  
 Kolekci dat lze seskupit, seřadit nebo filtrovat. WPF 4,5 umožňuje změnit uspořádání dat při změně dat. Předpokládejme například, že aplikace používá <xref:System.Windows.Controls.DataGrid> k vypsání zásob na burzovním trhu a zásoby jsou seřazené podle hodnoty zásob. Pokud je u <xref:System.Windows.Data.CollectionView>akcií povolených živé řazení, pozice na skladě v <xref:System.Windows.Controls.DataGrid> se přesune, když se hodnota akcie změní na větší nebo menší než hodnota jiné skladové položky.   Další informace najdete v tématu rozhraní <xref:System.ComponentModel.ICollectionViewLiveShaping>.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Vylepšená podpora pro navázání slabého odkazu na událost  
 Implementace slabého vzoru událostí je teď snazší, protože se k nim můžou zúčastnit předplatitelé události bez implementace dalšího rozhraní.  Obecná třída <xref:System.Windows.WeakEventManager> také umožňuje předplatitelům zapojit se do slabého vzoru události, pokud pro určitou událost neexistuje vyhrazený <xref:System.Windows.WeakEventManager>.  Další informace najdete v tématu [slabé vzory událostí](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nové metody pro třídu Dispatcher  
 Třída Dispatcher definuje nové metody pro synchronní a asynchronní operace.  Metoda synchronního <xref:System.Windows.Threading.Dispatcher.Invoke%2A> definuje přetížení, která přijímají parametr <xref:System.Action> nebo <xref:System.Func%601>. Nová asynchronní metoda, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, také přebírá <xref:System.Action> nebo <xref:System.Func%601> jako parametr zpětného volání a vrací <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>.   Třídy <xref:System.Windows.Threading.DispatcherOperation> a <xref:System.Windows.Threading.DispatcherOperation%601> definují vlastnost <xref:System.Threading.Tasks.Task>.  Když zavoláte <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, můžete použít klíčové slovo `await` s <xref:System.Windows.Threading.DispatcherOperation> nebo související <xref:System.Threading.Tasks.Task>. Pokud potřebujete počkat synchronně pro <xref:System.Threading.Tasks.Task>, která je vrácena <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, zavolejte metodu rozšíření <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>. Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> způsobí zablokování, pokud je operace zařazena do fronty volajícího vlákna. Další informace o použití <xref:System.Threading.Tasks.Task> k provádění asynchronních operací naleznete v tématu [Task paralelismus (Task Parallel Library)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Rozšíření značek pro události  
 WPF 4,5 podporuje rozšíření značek pro události.  I když WPF nedefinuje rozšíření značek, které se má použít pro události, třetí strany mohou vytvořit rozšíření značek, které lze použít s událostmi.  
  
## <a name="see-also"></a>Viz také:

- [Novinky v rozhraní .NET Framework](../../whats-new/index.md)
