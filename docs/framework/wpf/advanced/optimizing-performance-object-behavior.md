---
title: 'Optimalizace výkonu: Chování objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 67184db7fc1459e83ac7b1e6ff09ef56e43f0ca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187080"
---
# <a name="optimizing-performance-object-behavior"></a>Optimalizace výkonu: Chování objektu
Pochopení vnitřní chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů vám pomůže provést správné kompromisy mezi funkčností a výkonem.  

<a name="Not_Removing_Event_Handlers"></a>
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Neodebrání obslužné rutiny událostí u objektů může udržet objekty naživu  
 Delegát, který objekt předá jeho událost je účinně odkaz na tento objekt. Proto obslužné rutiny událostí můžete zachovat objekty naživu déle, než bylo očekáváno. Při čištění objektu, který se zaregistroval k naslouchání události objektu, je nezbytné odebrat tohoto delegáta před uvolněním objektu. Udržování nepotřebných objektů naživu zvyšuje využití paměti aplikace. To platí zejména v případě, že objekt je kořenlogického stromu nebo vizuální strom.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zavádí slabý vzor posluchače událostí pro události, které mohou být užitečné v situacích, kdy jsou vztahy životnosti objektu mezi zdrojem a posluchačem obtížně sledovat. Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existující události používají tento vzor. Pokud implementujete objekty s vlastní události, tento vzor může být použití pro vás. Podrobnosti naleznete [v tématu Slabé vzory událostí](weak-event-patterns.md).  
  
 Existuje několik nástrojů, jako je například CLR Profiler a pracovní sada Viewer, které mohou poskytuje informace o využití paměti zadaného procesu. Clr Profiler obsahuje řadu velmi užitečných zobrazení profilu přidělení, včetně histogramu přidělených typů, grafů přidělení a volání, časové osy zobrazující uvolňování paměti různých generací a výsledný stav spravované haldy po tyto kolekce a strom volání zobrazující přidělení metod a zatížení sestavení. Další informace naleznete v tématu [Performance](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>
## <a name="dependency-properties-and-objects"></a>Vlastnosti závislostí a objekty  
 Obecně platí přístup k vlastnosti <xref:System.Windows.DependencyObject> závislosti není pomalejší než přístup k clr vlastnost. Zatímco je malý výkon režie pro nastavení hodnoty vlastnosti, získání hodnoty je stejně rychlý jako získání hodnoty z clr vlastnost. Vyrovnání malé režie výkonu je skutečnost, že vlastnosti závislostí podporují robustní funkce, jako je například datové vazby, animace, dědičnosti a stylingu. Další informace naleznete v [tématu Přehled vlastností závislostí](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optimalizace vlastností závislostí  
 Ve vaší aplikaci byste měli definovat vlastnosti závislostí velmi pečlivě. Pokud <xref:System.Windows.DependencyProperty> váš vliv pouze vykreslit typ metadata možnosti, spíše než jiné možnosti metadat, jako je například <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, měli byste označit jako takové přepsáním jeho metadata. Další informace o přepsání nebo získání metadat vlastnosti naleznete v [tématu Metadata vlastností závislostí](dependency-property-metadata.md).  
  
 Může být efektivnější mít obslužnou rutinu změny vlastnosti zneplatnit míru, uspořádat a vykreslit průchody ručně, pokud ne všechny změny vlastností skutečně ovlivnit míru, uspořádat a vykreslit. Můžete se například rozhodnout znovu vykreslit pozadí pouze v případě, že hodnota je větší než nastavený limit. V takovém případě by obslužná rutina změny vlastnosti zneplatnila vykreslení pouze v případě, že hodnota překročí nastavený limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Vytvoření vlastnosti DependencyProperty dědičné není zdarma  
 Ve výchozím nastavení jsou vlastnosti registrované závislosti nedědičné. Můžete však explicitně provést libovolnou vlastnost dědičnou. I když se jedná o užitečnou funkci, převod vlastnosti dědičné ovlivňuje výkon zvýšením doby zneplatnění vlastnosti.  
  
### <a name="use-registerclasshandler-carefully"></a>Pečlivě používat RegisterClassHandler  
 Při <xref:System.Windows.EventManager.RegisterClassHandler%2A> volání umožňuje uložit stav instance, je důležité si uvědomit, že obslužná rutina je volána na každé instanci, což může způsobit problémy s výkonem. Používá <xref:System.Windows.EventManager.RegisterClassHandler%2A> se pouze v případě, že vaše aplikace vyžaduje uložení stavu instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Nastavení výchozí hodnoty vlastnosti DependencyProperty během registrace  
 Při vytváření, <xref:System.Windows.DependencyProperty> která vyžaduje výchozí hodnotu, nastavte hodnotu pomocí výchozímetadata předána jako parametr <xref:System.Windows.DependencyProperty.Register%2A> na metodu <xref:System.Windows.DependencyProperty>. Použijte tuto techniku spíše než nastavení hodnoty vlastnosti v konstruktoru nebo na každé instanci prvku.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Nastavení hodnoty PropertyMetadata pomocí registru  
 Při vytváření <xref:System.Windows.DependencyProperty>, máte možnost nastavit <xref:System.Windows.PropertyMetadata> pomocí <xref:System.Windows.DependencyProperty.Register%2A> buď <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody nebo. Přestože váš objekt může mít <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>statický konstruktor volat , to není optimální řešení a bude mít vliv na výkon. Chcete-li dosáhnout <xref:System.Windows.PropertyMetadata> nejlepšího výkonu, nastavte během volání na . <xref:System.Windows.DependencyProperty.Register%2A>  
  
<a name="Freezable_Objects"></a>
## <a name="freezable-objects"></a>Zmrazitelné objekty  
 A <xref:System.Windows.Freezable> je zvláštní typ objektu, který má dva stavy: nezmrazené a zmrazené. Zmrazení objektů, kdykoli je to možné, zlepšuje výkon aplikace a snižuje její pracovní sadu. Další informace naleznete v tématu [Přehled mrazivých objektů](freezable-objects-overview.md).  
  
 Každý <xref:System.Windows.Freezable> má <xref:System.Windows.Freezable.Changed> událost, která je vyvolána při každé změně. Oznámení o změnách jsou však nákladné z hlediska výkonu aplikace.  
  
 Zvažte následující příklad, <xref:System.Windows.Shapes.Rectangle> ve <xref:System.Windows.Media.Brush> kterém každý používá stejný objekt:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Ve výchozím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení poskytuje <xref:System.Windows.Media.SolidColorBrush> obslužnou rutinu události pro <xref:System.Windows.Freezable.Changed> událost objektu za účelem zrušení <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> platnosti vlastnosti objektu. V tomto případě pokaždé, když <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.Changed> má vyvolat jeho událost je nutné <xref:System.Windows.Shapes.Rectangle>vyvolat funkci zpětného volání pro každý – akumulace těchto vyvolání funkce zpětného volání uložit významné snížení výkonu. Kromě toho je velmi náročné na výkon přidat a odebrat obslužné rutiny v tomto okamžiku, protože aplikace by musel procházet celý seznam, aby tak učinily. Pokud váš scénář aplikace <xref:System.Windows.Media.SolidColorBrush>nikdy nezmění , budete platit <xref:System.Windows.Freezable.Changed> náklady na údržbu obslužné rutiny událostí zbytečně.  
  
 Zmrazení <xref:System.Windows.Freezable> může zlepšit jeho výkon, protože již není nutné vynaložit prostředky na údržbu oznámení o změně. V následující tabulce je uvedena <xref:System.Windows.Media.SolidColorBrush> velikost <xref:System.Windows.Freezable.IsFrozen%2A> jednoduchého, `true`pokud je jeho vlastnost nastavena na , ve srovnání s tím, kdy není. To předpokládá použití jedné <xref:System.Windows.Shapes.Shape.Fill%2A> stopy <xref:System.Windows.Shapes.Rectangle> na vlastnost deseti objektů.  
  
|**Stav**|**Velikost**|  
|---------------|--------------|  
|Zmrazené<xref:System.Windows.Media.SolidColorBrush>|212 bajtů|  
|Nezmrazené<xref:System.Windows.Media.SolidColorBrush>|972 bajtů|  
  
 Následující ukázka kódu ukazuje tento koncept:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Změněné obslužné rutiny na nezmrazených zmrazeních mohou udržovat objekty naživu  
 Delegát, který objekt předá <xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed> události objektu, je efektivně odkazem na tento objekt. Proto <xref:System.Windows.Freezable.Changed> obslužné rutiny událostí můžete zachovat objekty naživu déle, než bylo očekáváno. Při čištění objektu, který se zaregistroval k <xref:System.Windows.Freezable> naslouchání <xref:System.Windows.Freezable.Changed> události objektu, je nezbytné odebrat tohoto delegáta před uvolněním objektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také zavěsí <xref:System.Windows.Freezable.Changed> události interně. Například všechny vlastnosti závislostí, které <xref:System.Windows.Freezable> berou <xref:System.Windows.Freezable.Changed> jako hodnotu, budou automaticky poslouchat události. Vlastnost, <xref:System.Windows.Shapes.Shape.Fill%2A> která trvá <xref:System.Windows.Media.Brush>, ilustruje tento koncept.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Při přiřazení `myBrush` do `myRectangle.Fill`, delegát směřující <xref:System.Windows.Shapes.Rectangle> zpět na objekt <xref:System.Windows.Media.SolidColorBrush> bude přidán <xref:System.Windows.Freezable.Changed> k události objektu. To znamená, že následující `myRect` kód ve skutečnosti nečiní způsobilé pro uvolňování paměti:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 V tomto `myBrush` případě `myRectangle` je stále naživu a bude volat <xref:System.Windows.Freezable.Changed> zpět na něj, když požáry jeho událost. Všimněte si, `myBrush` <xref:System.Windows.Shapes.Shape.Fill%2A> že přiřazení <xref:System.Windows.Shapes.Rectangle> vlastnosti nového jednoduše `myBrush`přidá další obslužnou rutinu události do aplikace .  
  
 Doporučený způsob, jak vyčistit tyto typy objektů <xref:System.Windows.Media.Brush> je <xref:System.Windows.Shapes.Shape.Fill%2A> odebrat z vlastnosti, která bude zase odebrat obslužnou rutinu <xref:System.Windows.Freezable.Changed> události.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>
## <a name="user-interface-virtualization"></a>Virtualizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také poskytuje variantu <xref:System.Windows.Controls.StackPanel> prvku, který automaticky "virtualizuje" podřízený obsah vázaný na data. V tomto kontextu slovo virtualizovat odkazuje na techniku, kterou podmnožina objektů jsou generovány z většího počtu datových položek na základě položek, které jsou viditelné na obrazovce. Je intenzivní, a to jak z hlediska paměti a procesoru, generovat velké množství prvků uživatelského rozhraní, když pouze několik může být na obrazovce v daném okamžiku. <xref:System.Windows.Controls.VirtualizingStackPanel>(prostřednictvím funkce poskytované <xref:System.Windows.Controls.VirtualizingPanel>) vypočítá viditelné položky <xref:System.Windows.Controls.ItemContainerGenerator> a <xref:System.Windows.Controls.ItemsControl> pracuje <xref:System.Windows.Controls.ListBox> s <xref:System.Windows.Controls.ListView>z (například nebo ) vytvořit pouze prvky pro viditelné položky.  
  
 Jako optimalizace výkonu vizuální objekty pro tyto položky jsou generovány nebo udržovány naživu pouze v případě, že jsou viditelné na obrazovce. Pokud již nejsou v zobrazitelné oblasti ovládacího prvku, mohou být vizuální objekty odebrány. To není zaměňovat s virtualizace dat, kde datové objekty nejsou všechny přítomny v místní kolekci- spíše streamované v podle potřeby.  
  
 V následující tabulce je uveden uplynulý čas přidání <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.StackPanel> vykreslení <xref:System.Windows.Controls.VirtualizingStackPanel>5000 prvků do a a . V tomto scénáři představují měření čas mezi připojením <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> textového <xref:System.Windows.Controls.ItemsControl> řetězce k vlastnosti objektu k době, kdy prvky panelu zobrazují textový řetězec.  
  
|**Hostitelský panel**|**Doba vykreslení (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Viz také

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další doporučení k optimalizaci výkonu](optimizing-performance-other-recommendations.md)
