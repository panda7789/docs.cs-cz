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
ms.openlocfilehash: c599542668a2bbc4d13dbbf5590fdc50113a25af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521377"
---
# <a name="optimizing-performance-object-behavior"></a>Optimalizace výkonu: Chování objektu
Principy vnitřní chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty se vám pomůže zajistit správné kompromisy mezi funkčnosti a výkonu.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Může objekty zachování není odebírání obslužných rutin událostí na objekty  
 Delegát, který se předá objekt jeho událost je v podstatě odkaz na tento objekt. Proto obslužných rutin událostí můžete zachování objekty déle, než se očekávalo. Při provádění vyčištění objektu, který je zaregistrován k naslouchání události objektu, je nutné odebrat tento delegát před uvolněním objektu. Udržování nepotřebné objekty aktivní zvýší využití paměti vaší aplikace. To platí zejména při objektu je kořenem logického stromu nebo vizuálního stromu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] představuje vzor slabých událostí naslouchací proces událostí, které mohou být užitečné v situacích, kde je obtížné sledovat vztahy doba života objektů mezi zdrojem a naslouchacího procesu. Některé stávající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tento model použijte události. Při implementaci objekty s vlastní události, tento model může být použití vám. Podrobnosti najdete v tématu [slabé vzory událostí](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
 Existuje několik nástrojů, jako je Profiler CLR a práce nastavit prohlížeč, který může poskytuje informace o využití paměti určeného procesu. Profiler CLR zahrnuje několik velmi užitečné zobrazení přidělení profilu, včetně histogram přidělených typů, přidělování a volání grafů, časová osa zobrazuje uvolňování paměti kolekce různých generací a výsledný stav spravované haldě po Tato kolekce a strom volání na metodu přidělení a načítání sestavení. Další informace najdete v tématu [středisko pro vývojáře rozhraní .NET Framework](https://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Vlastnosti závislostí a objekty  
 Obecně platí, přístupem k vlastnosti závislostí <xref:System.Windows.DependencyObject> není pomalejší než přímý přístup k [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost. Při malé výkonu režie pro nastavení hodnoty vlastnosti hodnotu je tak rychle jako získávání hodnoty z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost. Vyrovnání zatížení výkonu je skutečnost, že vlastnosti závislosti podporují bohaté funkce, jako jsou datové vazby, animace, dědičnosti a stylu. Další informace najdete v tématu [přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Vlastnost DependencyProperty optimalizace  
 Vlastnosti závislosti ve své aplikaci byste měli definovat velmi opatrně. Pokud vaše <xref:System.Windows.DependencyProperty> ovlivňuje pouze vykreslit možnosti metadat typu, nikoli další metadata možnosti, jako <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, byste měli označit ji jako takové tak, že přepíšete jeho metadata. Další informace o přepsání nebo získání metadat vlastností najdete v tématu [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Může být efektivnější mít vlastnost změnit obslužnou rutinu zneplatnit míry, uspořádat a ručně vykreslení průchodů není-li všechny změny vlastností ve skutečnosti vliv na míru, uspořádání a vykreslování. Například můžete rozhodnout pouze v případě, že je hodnota větší než nastaveného limitu znovu zpracovat na pozadí. V takovém případě obslužné rutiny změny vlastnosti by pouze zneplatnit vykreslení Pokud hodnota přesahuje nastaveného limitu.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Provádění odvoditelný vlastnost DependencyProperty není volná  
 Ve výchozím nastavení registrované závislé vlastnosti jsou Neděditelný. Ale můžete explicitně provedete jakékoli vlastnosti odvoditelný. Když je užitečná funkce, převod vlastnost, která má být odvoditelný má vliv na výkon zvýšením dobu pro vlastnost zneplatnění.  
  
### <a name="use-registerclasshandler-carefully"></a>Používejte opatrně, RegisterClassHandler  
 Při volání <xref:System.Windows.EventManager.RegisterClassHandler%2A> umožňuje uložit stav vaší instance je důležité uvědomit si, že obslužná rutina je volána v každé instanci, což může způsobit problémy s výkonem. Používejte pouze <xref:System.Windows.EventManager.RegisterClassHandler%2A> když vaše aplikace vyžaduje uložení stavu vaší instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Nastavit výchozí hodnota pro DependencyProperty během registrace  
 Při vytváření <xref:System.Windows.DependencyProperty> , která vyžaduje výchozí hodnotu, nastavte hodnotu pomocí metadat výchozí předán jako parametr <xref:System.Windows.DependencyProperty.Register%2A> metodu <xref:System.Windows.DependencyProperty>. Použijte tento postup spíše než nastavení hodnoty vlastnosti v konstruktoru nebo pro každou instanci elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Třída PropertyMetadata hodnotu pomocí registru  
 Při vytváření <xref:System.Windows.DependencyProperty>, máte možnost nastavení <xref:System.Windows.PropertyMetadata> buď pomocí <xref:System.Windows.DependencyProperty.Register%2A> nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody. I když objekt může mít statický konstruktor pro volání <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, to není ideální řešení a bude mít vliv na výkon. Pro zajištění nejlepšího výkonu nastavte <xref:System.Windows.PropertyMetadata> během volání <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable – objekty  
 A <xref:System.Windows.Freezable> je speciální typ objektu, který má dva stavy: zmrazen a je zmrazen. Zmrazení objekty, kdykoli je to možné zlepšuje výkon vaší aplikace a snižuje jeho pracovní sady. Další informace najdete v tématu [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Každý <xref:System.Windows.Freezable> má <xref:System.Windows.Freezable.Changed> událost, která je vyvolána pokaždé, když se změní. Oznámení o změnách jsou však může být pracné výkon aplikace.  
  
 Podívejte se na následující příklad, ve nichž každý <xref:System.Windows.Shapes.Rectangle> používá stejná <xref:System.Windows.Media.Brush> objektu:  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje obslužné rutiny události <xref:System.Windows.Media.SolidColorBrush> objektu <xref:System.Windows.Freezable.Changed> událostí, aby bylo možné zneplatnit <xref:System.Windows.Shapes.Rectangle> objektu <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost. V takovém případě pokaždé, když <xref:System.Windows.Media.SolidColorBrush> musí vyvolat jeho <xref:System.Windows.Freezable.Changed> událostí, je potřeba vyvolat funkci zpětného volání pro každý <xref:System.Windows.Shapes.Rectangle>– akumulací těchto volání funkce zpětného volání kladou snížení výkonu. Kromě toho je velmi přidávat a odebírat obslužných rutin v tomto okamžiku, protože aplikace musel procházet celý seznam Uděláte to tak náročné na výkon. Pokud váš scénář aplikace se nikdy nemění <xref:System.Windows.Media.SolidColorBrush>, bude platit náklady na údržbu <xref:System.Windows.Freezable.Changed> obslužné rutiny událostí zbytečně.  
  
 Zmrazení <xref:System.Windows.Freezable> můžete vylepšit výkon, protože už nebude potřeba vynaložit prostředky týkající se zachování oznámení o změnách. Následující tabulka uvádí velikost jednoduchý <xref:System.Windows.Media.SolidColorBrush> při jeho <xref:System.Windows.Freezable.IsFrozen%2A> je nastavena na `true`, ve srovnání s Pokud není. Předpokladem je použití jednoho štětce, který se <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost deset <xref:System.Windows.Shapes.Rectangle> objekty.  
  
|**Stav**|**Velikost**|  
|---------------|--------------|  
|Zmrazené <xref:System.Windows.Media.SolidColorBrush>|212 bajtů|  
|Zmrazené bez <xref:System.Windows.Media.SolidColorBrush>|972 bajtů|  
  
 Následující příklad kódu demonstruje tento koncept.  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Změněné obslužné rutiny na nezmrazený Zablokovatelné může objekty zachování  
 Delegát, který se předá objekt <xref:System.Windows.Freezable> objektu <xref:System.Windows.Freezable.Changed> událost je v podstatě odkaz na tento objekt. Proto <xref:System.Windows.Freezable.Changed> obslužných rutin událostí můžete zachování objekty déle, než se očekávalo. Při provádění vyčištění objektu, který je zaregistrován k naslouchání <xref:System.Windows.Freezable> objektu <xref:System.Windows.Freezable.Changed> událostí, je nutné odebrat tento delegát před uvolněním objektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také zavěšení <xref:System.Windows.Freezable.Changed> události interně. Například všechny vlastnosti závislosti, což trvat <xref:System.Windows.Freezable> jako hodnotu bude naslouchat na <xref:System.Windows.Freezable.Changed> události automaticky. <xref:System.Windows.Shapes.Shape.Fill%2A> Vlastnost, která přijímá <xref:System.Windows.Media.Brush>, tento koncept znázorňuje.  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na přiřazení `myBrush` k `myRectangle.Fill`, delegát přejdete na zpět <xref:System.Windows.Shapes.Rectangle> objektu se přidají do <xref:System.Windows.Media.SolidColorBrush> objektu <xref:System.Windows.Freezable.Changed> událostí. To znamená, že následující kód Nedovolte, aby byly skutečně `myRect` nárok uvolňování paměti:  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 V tomto případě `myBrush` je zachovat `myRectangle` aktivní a zavolá zpět do něj při vyvolává jeho <xref:System.Windows.Freezable.Changed> událostí. Všimněte si, že přiřazení `myBrush` k <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost nové <xref:System.Windows.Shapes.Rectangle> bude jednoduše přidejte jinou obslužnou rutinu události pro `myBrush`.  
  
 Doporučeným způsobem, jak vyčistit tyto typy objektů je odebrat <xref:System.Windows.Media.Brush> z <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost, která se pak odebrat <xref:System.Windows.Freezable.Changed> obslužné rutiny události.  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje varianta <xref:System.Windows.Controls.StackPanel> element, který automaticky "Virtualizuje" vázané na data podřízený obsah. V tomto kontextu se toto slovo Virtualizovat odkazuje na technika, podle kterého jsou generovány podmnožiny objekty z větší počet datových položek na základě položky, které jsou viditelné na obrazovce. Je velmi náročná, jak z hlediska paměti a procesoru, ke generování velkého počtu prvků uživatelského rozhraní, pokud jen některé mohou být na obrazovce v daném okamžiku. <xref:System.Windows.Controls.VirtualizingStackPanel> (prostřednictvím funkce poskytované službou <xref:System.Windows.Controls.VirtualizingPanel>) vypočítá viditelné položky a funguje s <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (například <xref:System.Windows.Controls.ListBox> nebo <xref:System.Windows.Controls.ListView>) pouze vytvořit prvky viditelné položky.  
  
 Optimalizace výkonu jsou vizuální objekty pro tyto položky pouze generované nebo udržována nehledě v případě, že jsou viditelné na obrazovce. Když už nejsou v oblasti zobrazit ovládacího prvku, může být odebrán vizuální objekty. Toto je by se zaměňovat s virtualizací dat, ve kterém datové objekty nejsou všechny do místní kolekce-spíše datovým proudem, podle potřeby.  
  
 Následující tabulka ukazuje uplynulý čas, přidávání a vykreslování 5000 <xref:System.Windows.Controls.TextBlock> prvků, které mají <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.VirtualizingStackPanel>. V tomto scénáři měření představuje čas mezi textový řetězec pro připojení <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ItemsControl> objektu do doby, kdy prvky panel zobrazení textového řetězce.  
  
|**Panel hostitele**|**Vykreslení doba (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další výkonnostní doporučení](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
