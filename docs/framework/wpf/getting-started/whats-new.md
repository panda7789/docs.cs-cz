---
title: "Jaký & č. 39; s nové ve verzi WPF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: "55"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8de8725bc48f69cdd18100d90a1bc610caa7ecfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-wpf-version-45"></a>Jaký & č. 39; s nové ve verzi WPF 4.5
<a name="introduction"></a>Toto téma obsahuje informace o nových a vylepšených funkcích v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] verze 4.5.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Ovládací prvek pásu karet](#ribbon_control)  
  
-   [Lepší výkon při zobrazení velkého nastaví seskupené dat](#grouped_virtualization)  
  
-   [Nové funkce VirtualizingPanel](#VirtualizingPanel)  
  
-   [Vytvoření vazby na statické vlastnosti](#static_properties)  
  
-   [Přístup k kolekce na uživatelského rozhraní vláken](#xthread_access)  
  
-   [Synchronně a asynchronně ověřování dat](#INotifyDataErrorInfo)  
  
-   [Automaticky aktualizuje zdroj datová vazba](#delay)  
  
-   [Vytvoření vazby na typy této ICustomTypeProvider implementace](#ICustomTypeProvider)  
  
-   [Načítání informace o vazbě dat z výrazu vazby](#binding_state)  
  
-   [Kontrola platný objekt DataContext](#DisconnectedSource)  
  
-   [Přemístění dat, jak změnit hodnoty data (shaping za provozu)](#live_shaping)  
  
-   [Vylepšená podpora pro zřízení slabé odkaz na událost](#weak_event_pattern)  
  
-   [Nové metody pro třídu dispečera](#async)  
  
-   [Rozšíření značek pro události](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Ovládací prvek pásu karet  
 WPF 4.5 se dodává s <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvek, který je hostitelem nástrojů Rychlý přístup, nabídku aplikace a karty.  Další informace najdete v tématu [přehled pásu karet](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Lepší výkon při zobrazení velkého nastaví seskupené dat  
 Virtualizace uživatelského rozhraní nastane, když podmnožinu uživatelského rozhraní (UI) elementy generují z větší počet datových položek, podle které položky se viditelný na obrazovce. <xref:System.Windows.Controls.VirtualizingPanel> Definuje <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> přidružená vlastnost umožňující virtualizace uživatelského rozhraní pro seskupené data.  Další informace o seskupení dat najdete v tématu Postupy: řazení a skupinu dat pomocí zobrazení v jazyce XAML.  Další informace o virtualizaci seskupené data, najdete v části <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> přidružená vlastnost.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Nové funkce VirtualizingPanel  
  
1.  Můžete zadat zda <xref:System.Windows.Controls.VirtualizingPanel>, jako <xref:System.Windows.Controls.VirtualizingStackPanel>, zobrazí částečné položky pomocí <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> přidružená vlastnost. Pokud <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> je nastaven na <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> zobrazí pouze položky, které jsou zcela viditelné. Pokud <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> je nastaven na <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> částečně viditelné položky lze zobrazit.  
  
2.  Můžete zadat velikost mezipaměti před a po zobrazení při <xref:System.Windows.Controls.VirtualizingPanel> je virtualizace pomocí <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> přidružená vlastnost.  Mezipaměť je množství místa nad nebo pod zobrazovacího okna, ve které nejsou virtualizované položky.  Aby nedošlo ke generování prvky uživatelského rozhraní, jako jste přešli do zobrazení pomocí mezipaměti může zlepšit výkon. Mezipaměti se naplní s nižší prioritou, takže aplikace se nestane reagovat během operace. <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Vlastnost určuje jednotky měření, který je používán <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Vytvoření vazby na statické vlastnosti  
 Statické vlastnosti můžete použít jako zdroj dat vazby. Modul vazby dat rozpozná při změně hodnoty vlastnosti Pokud statické událost se vyvolá.  Například pokud třída `SomeClass` definuje statickou vlastnost s názvem `MyProperty`, `SomeClass` můžete definovat statické událost, která se vyvolá, když hodnota `MyProperty` změny.  Statické událostí můžete použít některý z následujících podpisů.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Všimněte si, že v prvním případě zpřístupní třídy statických událostí s názvem *PropertyName* `Changed` , předá <xref:System.EventArgs> k obslužné rutině událostí.  V druhém případě zpřístupní třída statické událost s názvem `StaticPropertyChanged` , předá <xref:System.ComponentModel.PropertyChangedEventArgs> k obslužné rutině událostí. Můžete zvolit třídu, která implementuje statickou vlastnost vyvolat změnu vlastnosti oznámení pomocí těchto metod.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Přístup k kolekce na uživatelského rozhraní vláken  
 WPF umožňuje přístup a úpravy kolekcí dat na vláken než ten, který vytvořil kolekce.  To umožňuje použití vlákna na pozadí a přijímat data z externího zdroje, jako je například databáze, zobrazení dat ve vlákně UI.  Pomocí jiné vlákno k úpravě kolekce, uživatelské rozhraní stále poměrně rychle reaguje na interakci s uživatelem.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Synchronně a asynchronně ověřování dat  
 <xref:System.ComponentModel.INotifyDataErrorInfo> Rozhraní umožňuje data entity třídy k implementaci vlastních ověřovacích pravidel a vystavit výsledky ověření asynchronně. Toto rozhraní podporuje také objekty vlastní chyby, několik chyb na vlastnost, mezi vlastnost chyb a chyb na úrovni entit.  Další informace naleznete v tématu <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Automaticky aktualizuje zdroj datová vazba  
 Pokud používáte datové vazby k aktualizaci zdroje dat, můžete použít <xref:System.Windows.Data.BindingBase.Delay%2A> vlastnosti a určit tak množství času předat po provedení změn vlastnosti v cílovém před aktualizací zdroje.  Předpokládejme například, že máte <xref:System.Windows.Controls.Slider> s jeho <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastnost data obousměrný vázány na vlastnost objekt dat a <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> je nastavena na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  V tomto příkladu, když se uživatel přesune <xref:System.Windows.Controls.Slider>, zdroj aktualizace pro každý pixelů, <xref:System.Windows.Controls.Slider> přesune.  Zdrojový objekt obvykle musí hodnota posuvník pouze tehdy, když posuvníku <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zastaví změna.  Aby zdroj aktualizace příliš často, použijte <xref:System.Windows.Data.BindingBase.Delay%2A> zdroj nesmí aktualizace, dokud množství času uplyne po úchytu zastaví přesunutí.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Vytvoření vazby na typy této ICustomTypeProvider implementace  
 WPF podporuje datovou vazbu na objekty, které implementují <xref:System.Reflection.ICustomTypeProvider>, označované také jako vlastní typy.  V následujících případech můžete použít vlastní typy.  
  
1.  Jako <xref:System.Windows.PropertyPath> v datové vazbě. Například <xref:System.Windows.Data.Binding.Path%2A> vlastnost <xref:System.Windows.Data.Binding> vlastností vlastního typu, můžete odkazovat.  
  
2.  Jako hodnotu <xref:System.Windows.DataTemplate.DataType%2A> vlastnost.  
  
3.  Jako typ, který určuje automaticky generované sloupců v <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Načítání informace o vazbě dat z výrazu vazby  
 V některých případech se mohou objevit <xref:System.Windows.Data.BindingExpression> z <xref:System.Windows.Data.Binding> a potřebujete informace o zdrojové a cílové objekty vazby.  Přibyla nová rozhraní API umožňují získat zdrojový nebo cílový objekt nebo přidružené vlastnosti.  Pokud máte <xref:System.Windows.Data.BindingExpression>, použijte následující rozhraní API a získat informace o zdrojové a cílové.  
  
|Tuto hodnotu najdete vazby|Použít toto rozhraní API|  
|---------------------------------------|------------------|  
|Cílový objekt|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Vlastnost target|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Zdrojový objekt|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Zdrojová vlastnost|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Jestli <xref:System.Windows.Data.BindingExpression> patří<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Vlastník<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Kontrola platný objekt DataContext  
 Existují případy, kdy <xref:System.Windows.FrameworkElement.DataContext%2A> z kontejner položek v <xref:System.Windows.Controls.ItemsControl> dojde k odpojení.  Kontejner položek je element uživatelského rozhraní, který zobrazí položky v <xref:System.Windows.Controls.ItemsControl>.  Když <xref:System.Windows.Controls.ItemsControl> data vázaná na kolekci kontejner položek se generuje pro každou položku. V některých případech jsou kontejnery položek vyřazeny z vizuálním stromu. Jsou dvě typickými případy, kde se odebere kontejner položek při odebrání položky ze zdrojové kolekce a když je povolena virtualizace na <xref:System.Windows.Controls.ItemsControl>. V těchto případech <xref:System.Windows.FrameworkElement.DataContext%2A> položky kontejneru je možnost sentinel objekt, který je vrácený <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> statickou vlastnost.  Byste měli zkontrolovat, zda <xref:System.Windows.FrameworkElement.DataContext%2A> rovná <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> objekt před přístupem k <xref:System.Windows.FrameworkElement.DataContext%2A> k položky kontejneru.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Přemístění dat, jak změnit hodnoty data (shaping za provozu)  
 Kolekce dat můžete seskupené, seřadit nebo filtrovat. WPF 4.5 umožňuje data k uspořádání změnit, pokud se mění data. Předpokládejme například, že aplikace používá <xref:System.Windows.Controls.DataGrid> seznam na trhu stock a populací jsou seřazené podle uložené hodnoty. Pokud za provozu řazení je povolená na se stavy <xref:System.Windows.Data.CollectionView>, stock pozice v <xref:System.Windows.Controls.DataGrid> přesune, když se stane hodnota skladových větší nebo menší než jiné stock hodnotu.   Další informace najdete v tématu <xref:System.ComponentModel.ICollectionViewLiveShaping> rozhraní.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Vylepšená podpora pro zřízení slabé odkaz na událost  
 Implementace vzoru slabé událostí je teď jednodušší, protože odběratele, kteří mají události mohou být součástí ho bez implementace navíc rozhraní.  Obecná <xref:System.Windows.WeakEventManager> třída taky umožňuje odběratelům nechat účastnit vzoru slabé událostí, pokud je vyhrazená <xref:System.Windows.WeakEventManager> neexistuje určité události.  Další informace najdete v tématu [slabé vzory událostí](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Nové metody pro třídu dispečera  
 Třída dispečera definuje nové metody pro synchronní a asynchronní operace.  Synchronní <xref:System.Windows.Threading.Dispatcher.Invoke%2A> metoda definuje přetížení, které provést <xref:System.Action> nebo <xref:System.Func%601> parametr. Nový asynchronní metody <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, také trvá <xref:System.Action> nebo <xref:System.Func%601> jako parametr pro zpětné volání a vrátí <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>.   <xref:System.Windows.Threading.DispatcherOperation> a <xref:System.Windows.Threading.DispatcherOperation%601> třídy definují <xref:System.Threading.Tasks.Task> vlastnost.  Při volání <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, můžete použít `await` – klíčové slovo s buď <xref:System.Windows.Threading.DispatcherOperation> nebo s přiřazenou třídou <xref:System.Threading.Tasks.Task>. Pokud potřebujete synchronně čekat <xref:System.Threading.Tasks.Task> , je vrácen rutinou <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, volání <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> metoda rozšíření. Volání metody <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> bude mít za následek zablokování Pokud operaci ve frontě na volající vlákno. Další informace o používání <xref:System.Threading.Tasks.Task> k provedení asynchronních operací, najdete v části [paralelismus (Task Parallel Library)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Rozšíření značek pro události  
 WPF 4.5 podporuje rozšíření značek pro události.  Při WPF nedefinuje rozšíření značek pro události, budou moci vytvořit rozšíření značek, které je možné s událostmi třetím stranám.  
  
## <a name="see-also"></a>Viz také  
 [Novinky v rozhraní .NET Framework](../../../../docs/framework/whats-new/index.md)
