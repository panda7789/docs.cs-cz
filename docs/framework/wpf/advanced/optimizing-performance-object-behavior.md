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
ms.openlocfilehash: 025c8691eb1aaf9483a222530a5590670ede486b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400465"
---
# <a name="optimizing-performance-object-behavior"></a>Optimalizace výkonu: Chování objektu
Porozumění vnitřnímu chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů vám pomůže se zajištěním správného kompromisů mezi funkcemi a výkonem.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Neodebrání obslužných rutin událostí pro objekty může zachovat objekty v aktivním stavu.  
 Delegát, který objekt předává do své události, je efektivně odkaz na tento objekt. Proto obslužné rutiny událostí mohou udržet objekty po delší dobu, než se očekávalo. Při provádění vyčištění objektu, který je zaregistrován pro naslouchání události objektu, je nezbytné odebrat tohoto delegáta před uvolněním objektu. Zachování nepotřebných objektů zvyšuje využití paměti aplikace. To platí zejména v případě, že je objekt kořenem logického stromu nebo vizuálního stromu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zavádí slabý vzor naslouchacího procesu události pro události, které mohou být užitečné v situacích, kdy relace životního cyklu objektu mezi zdrojem a naslouchacím rozhraním nejsou obtížné sledovat. Tento model [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používají některé existující události. Pokud implementujete objekty s vlastními událostmi, je možné, že tento model bude použit pro vás. Podrobnosti najdete v tématu [slabé vzory událostí](weak-event-patterns.md).  
  
 Existuje několik nástrojů, například Profiler CLR a pracovní sada, které mohou poskytovat informace o využití paměti u zadaného procesu. Profiler CLR obsahuje řadu velmi užitečných zobrazení profilu přidělení, včetně histogramu přidělených typů, grafů přidělení a volání, časová osa zobrazující uvolňování paměti různých generací a výsledný stav spravované haldy po Tyto kolekce a strom volání znázorňující přidělení jednotlivých metod a načtení sestavení. Další informace najdete v tématu [Centrum pro vývojáře .NET Framework](https://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Vlastnosti a objekty závislosti  
 Obecně platí, že přístup k vlastnosti závislosti pro <xref:System.Windows.DependencyObject> není pomalejší než přístup k vlastnosti CLR. I když existuje malé nároky na výkon pro nastavení hodnoty vlastnosti, získání hodnoty je tak rychlé jako získání hodnoty z vlastnosti CLR. Snížení režijních nákladů na výkon je skutečnost, že vlastnosti závislosti podporují robustní funkce, jako jsou datové vazby, animace, dědičnost a stylování. Další informace najdete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optimalizace DependencyProperty  
 V aplikaci byste měli definovat vlastnosti závislostí velmi pečlivě. Pokud má <xref:System.Windows.DependencyProperty> vaše aplikace vliv pouze na možnosti metadat typu vykreslování, nikoli na jiné možnosti <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>metadat, jako například, byste ji měli označit tak, že přepíše její metadata. Další informace o přepsání nebo získání metadat vlastností naleznete v tématu [metadata vlastnosti závislosti](dependency-property-metadata.md).  
  
 Může být efektivnější, aby obslužná rutina změny vlastnosti neověřovala míru, sestavila a vygenerovala průchody ručně, pokud nejsou všechny změny vlastností nijak ovlivněny měřením, uspořádáním a vykreslováním. Například se můžete rozhodnout znovu vykreslit pozadí pouze v případě, že je hodnota větší než nastavený limit. V takovém případě by obslužná rutina změny vlastnosti neověřovala pouze vykreslení, pokud hodnota překročí nastavený limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Vytvoření dědičné vlastnosti DependencyProperty není volné.  
 Ve výchozím nastavení jsou zaregistrované vlastnosti závislosti nedědičné. Můžete ale explicitně nastavit vlastnost dědění. I když se jedná o užitečnou funkci, převod vlastnosti tak, aby bylo možné dědit dopad, tím, že se zvýší doba pro neplatnost vlastností.  
  
### <a name="use-registerclasshandler-carefully"></a>Používejte RegisterClassHandler pečlivě  
 Při volání <xref:System.Windows.EventManager.RegisterClassHandler%2A> umožňuje uložit stav instance, je důležité vědět, že je obslužná rutina volána na všech instancích, což může způsobit problémy s výkonem. Použijte <xref:System.Windows.EventManager.RegisterClassHandler%2A> pouze v případě, že vaše aplikace vyžaduje uložení stavu instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Nastavení výchozí hodnoty pro DependencyProperty během registrace  
 Při vytváření <xref:System.Windows.DependencyProperty> objektu, který vyžaduje výchozí hodnotu, nastavte hodnotu pomocí výchozích metadat předaných jako parametr <xref:System.Windows.DependencyProperty.Register%2A> metodě <xref:System.Windows.DependencyProperty>. Použijte tuto techniku namísto nastavení hodnoty vlastnosti v konstruktoru nebo v každé instanci elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Nastavení hodnoty hodnotu PropertyMetadata pomocí registru  
 Při vytváření <xref:System.Windows.DependencyProperty>můžete mít možnost <xref:System.Windows.PropertyMetadata> nastavení použít buď <xref:System.Windows.DependencyProperty.Register%2A> pomocí metody, nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> . I když váš objekt může mít statický konstruktor pro volání <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, nejedná se o optimální řešení a bude mít vliv na výkon. Pro nejlepší výkon nastavte <xref:System.Windows.PropertyMetadata> při <xref:System.Windows.DependencyProperty.Register%2A>volání metody.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Objekty Freezable  
 A <xref:System.Windows.Freezable> je speciální typ objektu, který má dva stavy: nezmrazené a zmrazené. Zamrznutí objekty vždy, když je to možné, zlepšuje výkon aplikace a snižuje její pracovní sadu. Další informace najdete v tématu [Přehled objektů Freezable](freezable-objects-overview.md).  
  
 <xref:System.Windows.Freezable> Každé<xref:System.Windows.Freezable.Changed> má událost, která je vyvolána pokaždé, když se změní. Oznámení o změně je však nákladné z pohledu výkonu aplikace.  
  
 Vezměte v úvahu následující příklad, ve <xref:System.Windows.Shapes.Rectangle> kterém každý používá <xref:System.Windows.Media.Brush> stejný objekt:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje obslužnou rutinu události <xref:System.Windows.Media.SolidColorBrush> pro <xref:System.Windows.Freezable.Changed> událost objektu, aby bylo možné zrušit platnost <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnosti objektu. V tomto případě je pokaždé, <xref:System.Windows.Media.SolidColorBrush> když musí <xref:System.Windows.Freezable.Changed> vyvolat událost, je nutné vyvolat funkci zpětného volání pro každý <xref:System.Windows.Shapes.Rectangle>– hromadění těchto volání funkce zpětného volání může způsobit výrazné snížení výkonu. Kromě toho je velmi náročné na výkon při přidávání a odebírání obslužných rutin v tomto okamžiku, protože aplikace by musela procházet celý seznam. Pokud váš scénář aplikace nikdy nemění <xref:System.Windows.Media.SolidColorBrush>, budete platit náklady na údržbu <xref:System.Windows.Freezable.Changed> obslužných rutin událostí zbytečně.  
  
 Zmrazení <xref:System.Windows.Freezable> může zlepšit jeho výkon, protože už nepotřebuje vysílat prostředky na údržbu oznámení změn. Následující tabulka ukazuje velikost jednoduchého <xref:System.Windows.Media.SolidColorBrush> , když je jeho <xref:System.Windows.Freezable.IsFrozen%2A> vlastnost nastavena na `true`, v porovnání s tím, že není. Předpokládá se použití jednoho štětce na <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost deseti <xref:System.Windows.Shapes.Rectangle> objektů.  
  
|**Stav**|**Hodnota**|  
|---------------|--------------|  
|Zmrazené<xref:System.Windows.Media.SolidColorBrush>|212 bajtů|  
|Nezmrazené<xref:System.Windows.Media.SolidColorBrush>|972 bajtů|  
  
 Následující ukázka kódu demonstruje tento koncept:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Změněné obslužné rutiny u nezmrazených Zablokovatelné můžou zachovat objekty v aktivním stavu.  
 Delegát, který objekt předává <xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed> události objektu, je efektivně odkaz na tento objekt. Proto obslužné <xref:System.Windows.Freezable.Changed> rutiny událostí mohou udržet objekty po delší dobu, než se očekávalo. Při provádění vyčištění objektu, který je zaregistrován pro naslouchání <xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed> události objektu, je nezbytné odebrat tohoto delegáta před uvolněním objektu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také zapojovat <xref:System.Windows.Freezable.Changed> události interně. Například všechny vlastnosti závislosti, které převezmou <xref:System.Windows.Freezable> hodnotu, budou automaticky <xref:System.Windows.Freezable.Changed> naslouchat událostem. Vlastnost, která <xref:System.Windows.Media.Brush>přebírá, představuje tento koncept. <xref:System.Windows.Shapes.Shape.Fill%2A>  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 U `myBrush` přiřazení k `myRectangle.Fill` objektubude<xref:System.Windows.Shapes.Rectangle> delegát ukazující zpátky na objekt přidán do <xref:System.Windows.Media.SolidColorBrush> událostiobjektu.<xref:System.Windows.Freezable.Changed> To znamená, že následující kód ve skutečnosti `myRect` nemá nárok na uvolňování paměti:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 V tomto případě `myBrush` je `myRectangle` stále Keep Alive a při spuštění <xref:System.Windows.Freezable.Changed> události vrátí do něj volání. Všimněte si, `myBrush` že přiřazení <xref:System.Windows.Shapes.Shape.Fill%2A> k vlastnosti nového <xref:System.Windows.Shapes.Rectangle> bude jednoduše přidat další obslužnou rutinu události `myBrush`do.  
  
 Doporučeným způsobem, jak tyto typy objektů vyčistit, je odebrat <xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A> z vlastnosti vlastnost, která zase odstraní <xref:System.Windows.Freezable.Changed> obslužnou rutinu události.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]také poskytuje variaci prvku, <xref:System.Windows.Controls.StackPanel> který automaticky "virtualizuje" podřízený obsah vázaný na data. V tomto kontextu slovo Virtualization odkazuje na techniku, podle které je vygenerována podmnožina objektů z většího počtu datových položek na základě toho, které položky jsou viditelné na obrazovce. Je náročné, a to jak z paměti, tak i procesoru, aby vygeneroval velký počet prvků uživatelského rozhraní, když na obrazovce v daném okamžiku může být jenom pár. <xref:System.Windows.Controls.VirtualizingStackPanel>(díky funkcím, <xref:System.Windows.Controls.VirtualizingPanel>které poskytuje) vypočítá viditelné položky a pracuje <xref:System.Windows.Controls.ItemContainerGenerator> s <xref:System.Windows.Controls.ListBox> z <xref:System.Windows.Controls.ItemsControl> a (například nebo <xref:System.Windows.Controls.ListView>), aby bylo možné vytvářet pouze prvky pro viditelné položky.  
  
 V rámci optimalizace výkonu jsou vizuální objekty pro tyto položky vygenerovány nebo udržovány pouze v případě, že jsou viditelné na obrazovce. Pokud již nejsou v zobrazitelné oblasti ovládacího prvku, může dojít k odebrání vizuálních objektů. Nemusíte se zaměňovat s virtualizací dat, kde datové objekty nejsou v místní kolekci přítomné, a to místo streamování v případě potřeby.  
  
 Následující tabulka ukazuje uplynulý čas přidávání a vykreslování elementů 5000 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel> do a <xref:System.Windows.Controls.VirtualizingStackPanel>. V tomto scénáři měření představuje čas mezi připojením textového řetězce k <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnosti <xref:System.Windows.Controls.ItemsControl> objektu k času, kdy prvky panelu zobrazují textový řetězec.  
  
|**Panel hostitele**|**Čas vykreslování (MS)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
