---
title: "Optimalizace výkonu: Chování objektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e929ec927bc0eb7494d8865fc5452cfc6910169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-object-behavior"></a>Optimalizace výkonu: Chování objektu
Principy vnitřní chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty pomůže vám správné kompromisy mezi funkcí a výkonu.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Může objekty zachování není odebrání obslužné rutiny událostí na objekty  
 Odkaz na tento objekt je efektivně delegáta, který objekt předá jeho událost. Proto obslužné rutiny událostí můžete zachovat objekty zachování déle, než se očekávalo. Při provádění vyčištění objektu, který je zaregistrovaná pro naslouchání na objektu události, je nezbytné k odebrání tohoto delegáta před uvolněním objektu. Zachování nepotřebné objekty zachování zvyšuje využití paměti aplikaci. To platí hlavně pokud je objekt kořen logického stromu nebo vizuálním stromu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]představuje vzor naslouchací proces slabé události pro události, které může být užitečné v situacích, kde je obtížné sledovat vztahy životnosti objektů mezi zdrojem a naslouchací proces. Některé stávající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události pomocí tohoto vzoru. Pokud implementujete objekty s vlastní události, může být tento vzor použití vám. Podrobnosti najdete v tématu [slabé vzory událostí](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
 Je několik nástrojů, jako je například profileru CLR a práce nastavte prohlížeč, můžete poskytující informace o využití paměti zadané procesu. Zahrnuje několik velmi užitečné zobrazení přidělení profilu, včetně histogram přidělené typy, přidělení a volání grafů, časová osa zobrazení kolekce různých generací a výsledný stav spravovaná halda po CLR profileru Tyto kolekce a volání stromu zobrazující za metoda přidělování a načítání sestavení. Další informace najdete v tématu [rozhraní .NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Vlastnosti závislosti a objekty  
 Obecně platí, přístupu k vlastnosti závislosti <xref:System.Windows.DependencyObject> není pomalejší než přístup k [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost. Zatímco je malý výkonu režie pro nastavení hodnoty vlastnosti, získávání hodnotu je tak rychlý jako získávání hodnotu z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost. Odsazení malé zatížení je fakt, že vlastností závislostí podporují robustní funkce, například datové vazby, animace, dědičnost a stylů. Další informace najdete v tématu [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Vlastnost DependencyProperty optimalizace  
 Vlastnosti závislosti ve vaší aplikaci byste měli definovat velmi opatrně. Pokud vaše <xref:System.Windows.DependencyProperty> ovlivňuje pouze vykreslit možnosti metadata typu, nikoli další možnosti metadata, jako <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, byste měli označit ji jako takový přepsáním jeho metadata. Další informace o přepsání nebo získání metadat vlastností najdete v tématu [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Může být efektivnější vlastnost změnu obslužná rutina zneplatnit míry, uspořádání a vykreslit předává ručně není-li všechny změny vlastností ve skutečnosti ovlivnit měr, uspořádání a vykreslit. Například můžete se rozhodnout opakovaně vykreslit pozadí jenom v případě, že je hodnota větší než nastaveného limitu. V takovém případě vaší obslužné rutiny změnit vlastnost by pouze zneplatnit vykreslení Pokud hodnota přesahuje nastaveného limitu.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Provedení vlastnost DependencyProperty zděditelné nemá volná  
 Ve výchozím nastavení jsou Neděditelný vlastností registrované závislostí. Však můžete explicitně nastavit vlastnost zděditelné. To je užitečné funkce, převod vlastnost, která má být zděditelné zvýšením dobu pro vlastnost zneplatnění ovlivňuje výkon.  
  
### <a name="use-registerclasshandler-carefully"></a>Pečlivě dodržujte RegisterClassHandler  
 Při volání <xref:System.Windows.EventManager.RegisterClassHandler%2A> umožňuje uložit stav vaší instance je důležité si uvědomit, že je obslužná rutina na každou instanci, která může způsobit problémy s výkonem. Používat pouze <xref:System.Windows.EventManager.RegisterClassHandler%2A> když vaše aplikace vyžaduje, abyste uložili vašeho stav instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Nastavit výchozí hodnotu pro vlastnost DependencyProperty během registrace  
 Při vytváření <xref:System.Windows.DependencyProperty> vyžadující výchozí hodnotu, nastavte hodnotu pomocí metadat výchozí předány jako parametr, který se <xref:System.Windows.DependencyProperty.Register%2A> metodu <xref:System.Windows.DependencyProperty>. Použijte tento postup spíše než nastavení hodnoty vlastnosti v konstruktoru nebo na každou instanci elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Nastavte hodnotu PropertyMetadata pomocí registrace  
 Při vytváření <xref:System.Windows.DependencyProperty>, máte možnost nastavení <xref:System.Windows.PropertyMetadata> buď pomocí <xref:System.Windows.DependencyProperty.Register%2A> nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody. I když objektu může být statického konstruktoru volat <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, to není optimální řešení a bude mít vliv na výkon. Pro nejlepší výkon, nastavte <xref:System.Windows.PropertyMetadata> během volání <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Zmrazitelné objekty  
 A <xref:System.Windows.Freezable> je zvláštní typ objektu, který má dva stavy: zmrazen a pozastaveny. Zmrazení objekty kdykoli je to možné vylepšuje výkon aplikace a snižuje jeho pracovní sady. Další informace najdete v tématu [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Každý <xref:System.Windows.Freezable> má <xref:System.Windows.Freezable.Changed> událost, která se vyvolá, vždy, když se změní. Oznámení o změnách jsou však náročné na výkon aplikace.  
  
 Podívejte se na následující příklad, ve které každý <xref:System.Windows.Shapes.Rectangle> používá stejnou <xref:System.Windows.Media.Brush> objektu:  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje obslužné rutiny události pro <xref:System.Windows.Media.SolidColorBrush> objektu <xref:System.Windows.Freezable.Changed> událostí, aby bylo možné zrušit platnost <xref:System.Windows.Shapes.Rectangle> objektu <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost. V takovém případě pokaždé, když <xref:System.Windows.Media.SolidColorBrush> se má provést jeho <xref:System.Windows.Freezable.Changed> událostí je vyžadovaná k vyvolání funkce zpětného volání pro každou <xref:System.Windows.Shapes.Rectangle>– nahromadění těchto volání funkce zpětného volání použít snížení výkonu významné. Kromě toho je velmi náročná přidávat a odebírat obslužné rutiny v tomto okamžiku vzhledem k tomu, že aplikace by pak bylo procházení celý seznam Uděláte to tak výkon. Pokud váš scénář aplikace nikdy změní <xref:System.Windows.Media.SolidColorBrush>, bude platícího náklady na údržbu <xref:System.Windows.Freezable.Changed> obslužné rutiny událostí zbytečně.  
  
 Zmrazení <xref:System.Windows.Freezable> může zvýšit jeho výkon, protože už je nutné rozbalte uzel prostředky na údržbu oznámení o změnách. Následující tabulka uvádí velikost jednoduchou <xref:System.Windows.Media.SolidColorBrush> při jeho <xref:System.Windows.Freezable.IsFrozen%2A> je nastavena na `true`, ve srovnání se při není. Předpokladem je použití jednoho štětce k <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost deset <xref:System.Windows.Shapes.Rectangle> objekty.  
  
|**Stav**|**Velikost**|  
|---------------|--------------|  
|Pozastaveny<xref:System.Windows.Media.SolidColorBrush>|212 bajtů|  
|Bez pozastaveny<xref:System.Windows.Media.SolidColorBrush>|972 bajtů|  
  
 Následující příklad kódu ukazuje tento koncept:  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Změněné obslužné rutiny na nefixované Freezables může objekty zachování  
 Delegáta, který předá objekt <xref:System.Windows.Freezable> objektu <xref:System.Windows.Freezable.Changed> událostí je efektivně odkaz na tento objekt. Proto <xref:System.Windows.Freezable.Changed> obslužné rutiny událostí můžete zachovat objekty zachování déle, než se očekávalo. Při provádění vyčištění objektu, která je zaregistrovaná pro naslouchání na <xref:System.Windows.Freezable> objektu <xref:System.Windows.Freezable.Changed> událostí, je nezbytné k odebrání tohoto delegáta před uvolněním objektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také zachytí <xref:System.Windows.Freezable.Changed> události interně. Například všechny vlastnosti závislosti, které trvat <xref:System.Windows.Freezable> jako hodnotu bude naslouchat na <xref:System.Windows.Freezable.Changed> události automaticky. <xref:System.Windows.Shapes.Shape.Fill%2A> Vlastnost, která přebírá <xref:System.Windows.Media.Brush>, tento princip je zobrazen.  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na přiřazení `myBrush` k `myRectangle.Fill`, přejdete zpět na delegáta <xref:System.Windows.Shapes.Rectangle> objekt bude přidán k <xref:System.Windows.Media.SolidColorBrush> objektu <xref:System.Windows.Freezable.Changed> událostí. To znamená, že následující kód neprovádí ve skutečnosti `myRect` vhodné pro uvolňování paměti:  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 V takovém případě `myBrush` je stále uchovávání `myRectangle` aktivní a bude zpětného volání k němu když se aktivuje její <xref:System.Windows.Freezable.Changed> událostí. Všimněte si, že přiřazení `myBrush` k <xref:System.Windows.Shapes.Shape.Fill%2A> novou vlastnost <xref:System.Windows.Shapes.Rectangle> bude jednoduše přidejte jinou obslužnou rutinu události pro `myBrush`.  
  
 Doporučeným způsobem, jak vyčistit tyto typy objektů, které se má odebrat <xref:System.Windows.Media.Brush> z <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnosti, která zase odstraní <xref:System.Windows.Freezable.Changed> obslužné rutiny události.  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také poskytuje varianta <xref:System.Windows.Controls.StackPanel> element, který automaticky "Virtualizuje" obsah podřízené vázané na data. V tomto kontextu slovo Virtualizovat odkazuje na techniku, podle kterého se generují podmnožinu objektů větší počet datových položek na základě položek, které jsou viditelné na obrazovce. Je náročné, jak z hlediska paměti a procesoru k vygenerování velkého počtu prvky uživatelského rozhraní při jen několik může být na obrazovce v daném okamžiku. <xref:System.Windows.Controls.VirtualizingStackPanel>(prostřednictvím funkce poskytované službou <xref:System.Windows.Controls.VirtualizingPanel>) vypočítá viditelné položky a funguje s <xref:System.Windows.Controls.ItemContainerGenerator> z <xref:System.Windows.Controls.ItemsControl> (například <xref:System.Windows.Controls.ListBox> nebo <xref:System.Windows.Controls.ListView>) pouze vytvořit elementů pro položky viditelné.  
  
 Jako optimalizace výkonu vizuální objekty pro tyto položky jsou pouze generována nebo zachovány zachování připojení, pokud jsou viditelné na obrazovce. Když jsou už v oblasti zobrazitelné ovládacího prvku, může být odebrán vizuální objekty. Toto je Nezaměňovat s virtualizací datových, kde datové objekty nejsou všechny obsažené v místní kolekce-místo datovým proudem, podle potřeby.  
  
 Následující tabulka uvádí času, po přidání a vykreslování 5000 <xref:System.Windows.Controls.TextBlock> elementů <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.VirtualizingStackPanel>. V tomto scénáři se zjištěnými hodnotami představují čas mezi připojení textový řetězec <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ItemsControl> objektu na čas, kdy prvky panelů zobrazit textový řetězec.  
  
|**Panel hostitele**|**Vykreslení čas (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a vytvoření bitové kopie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další doporučení výkonu](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
