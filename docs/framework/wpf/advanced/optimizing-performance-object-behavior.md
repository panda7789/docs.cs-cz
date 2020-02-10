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
ms.openlocfilehash: 64e567cd28e9458b483b0963e0dedd924ad23bab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094485"
---
# <a name="optimizing-performance-object-behavior"></a>Optimalizace výkonu: Chování objektu
Porozumění vnitřnímu chování objektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vám pomůže zajistit, aby mezi funkcemi a výkonem byly správné kompromisy.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Neodebrání obslužných rutin událostí pro objekty může zachovat objekty v aktivním stavu.  
 Delegát, který objekt předává do své události, je efektivně odkaz na tento objekt. Proto obslužné rutiny událostí mohou udržet objekty po delší dobu, než se očekávalo. Při provádění vyčištění objektu, který je zaregistrován pro naslouchání události objektu, je nezbytné odebrat tohoto delegáta před uvolněním objektu. Zachování nepotřebných objektů zvyšuje využití paměti aplikace. To platí zejména v případě, že je objekt kořenem logického stromu nebo vizuálního stromu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zavádí slabý vzor naslouchacího procesu událostí pro události, které mohou být užitečné v situacích, kdy relace životního cyklu objektu mezi zdrojem a naslouchacím rozhraním nezpůsobí udržení přehledu o. Tento model používají některé existující události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pokud implementujete objekty s vlastními událostmi, je možné, že tento model bude použit pro vás. Podrobnosti najdete v tématu [slabé vzory událostí](weak-event-patterns.md).  
  
 Existuje několik nástrojů, například Profiler CLR a pracovní sada, které mohou poskytovat informace o využití paměti u zadaného procesu. Profiler CLR obsahuje řadu velmi užitečných zobrazení profilu přidělení, včetně histogramu přidělených typů, grafů přidělení a volání, časová osa zobrazující uvolňování paměti různých generací a výsledný stav spravované haldy po Tyto kolekce a strom volání znázorňující přidělení jednotlivých metod a načtení sestavení. Další informace najdete v tématu [výkon](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Vlastnosti a objekty závislosti  
 Obecně platí, že přístup k vlastnosti závislosti <xref:System.Windows.DependencyObject> není pomalejší než přístup k vlastnosti CLR. I když existuje malé nároky na výkon pro nastavení hodnoty vlastnosti, získání hodnoty je tak rychlé jako získání hodnoty z vlastnosti CLR. Snížení režijních nákladů na výkon je skutečnost, že vlastnosti závislosti podporují robustní funkce, jako jsou datové vazby, animace, dědičnost a stylování. Další informace najdete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Optimalizace DependencyProperty  
 V aplikaci byste měli definovat vlastnosti závislostí velmi pečlivě. Pokud má <xref:System.Windows.DependencyProperty> vliv pouze na možnosti metadat typu vykreslování, nikoli na jiné možnosti metadat, jako je například <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, měli byste jej označit tak, že přepíše jeho metadata. Další informace o přepsání nebo získání metadat vlastností naleznete v tématu [metadata vlastnosti závislosti](dependency-property-metadata.md).  
  
 Může být efektivnější, aby obslužná rutina změny vlastnosti neověřovala míru, sestavila a vygenerovala průchody ručně, pokud nejsou všechny změny vlastností nijak ovlivněny měřením, uspořádáním a vykreslováním. Například se můžete rozhodnout znovu vykreslit pozadí pouze v případě, že je hodnota větší než nastavený limit. V takovém případě by obslužná rutina změny vlastnosti neověřovala pouze vykreslení, pokud hodnota překročí nastavený limit.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Vytvoření dědičné vlastnosti DependencyProperty není volné.  
 Ve výchozím nastavení jsou zaregistrované vlastnosti závislosti nedědičné. Můžete ale explicitně nastavit vlastnost dědění. I když se jedná o užitečnou funkci, převod vlastnosti tak, aby bylo možné dědit dopad, tím, že se zvýší doba pro neplatnost vlastností.  
  
### <a name="use-registerclasshandler-carefully"></a>Používejte RegisterClassHandler pečlivě  
 Při volání <xref:System.Windows.EventManager.RegisterClassHandler%2A> umožňuje uložit stav instance, je důležité vědět, že je obslužná rutina volána na všech instancích, což může způsobit problémy s výkonem. <xref:System.Windows.EventManager.RegisterClassHandler%2A> použít pouze v případě, že vaše aplikace vyžaduje uložení stavu instance.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Nastavení výchozí hodnoty pro DependencyProperty během registrace  
 Při vytváření <xref:System.Windows.DependencyProperty>, která vyžaduje výchozí hodnotu, nastavte hodnotu pomocí výchozích metadat předaných jako parametr metodě <xref:System.Windows.DependencyProperty.Register%2A> <xref:System.Windows.DependencyProperty>. Použijte tuto techniku namísto nastavení hodnoty vlastnosti v konstruktoru nebo v každé instanci elementu.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Nastavení hodnoty hodnotu PropertyMetadata pomocí registru  
 Při vytváření <xref:System.Windows.DependencyProperty>máte možnost nastavit <xref:System.Windows.PropertyMetadata> pomocí <xref:System.Windows.DependencyProperty.Register%2A> nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>ch metod. I když váš objekt může mít statický konstruktor pro volání <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, nejedná se o optimální řešení a bude mít vliv na výkon. Pro dosažení nejlepšího výkonu nastavte <xref:System.Windows.PropertyMetadata> během volání <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Objekty Freezable  
 <xref:System.Windows.Freezable> je speciální typ objektu, který má dva stavy: nezmrazené a zmrazené. Zamrznutí objekty vždy, když je to možné, zlepšuje výkon aplikace a snižuje její pracovní sadu. Další informace najdete v tématu [Přehled objektů Freezable](freezable-objects-overview.md).  
  
 Každé <xref:System.Windows.Freezable> má <xref:System.Windows.Freezable.Changed> událost, která je vyvolána při každé změně. Oznámení o změně je však nákladné z pohledu výkonu aplikace.  
  
 Vezměte v úvahu následující příklad, ve kterém každý <xref:System.Windows.Shapes.Rectangle> používá stejný objekt <xref:System.Windows.Media.Brush>:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje obslužnou rutinu události pro událost <xref:System.Windows.Freezable.Changed> objektu <xref:System.Windows.Media.SolidColorBrush>, aby bylo možné neověřit vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A> objektu <xref:System.Windows.Shapes.Rectangle>. V tomto případě, pokaždé, když <xref:System.Windows.Media.SolidColorBrush> musí vyvolat svoji <xref:System.Windows.Freezable.Changed> událost, je nutné vyvolat funkci zpětného volání pro každý <xref:System.Windows.Shapes.Rectangle>– akumulace těchto funkcí zpětného volání může způsobit výrazné snížení výkonu. Kromě toho je velmi náročné na výkon při přidávání a odebírání obslužných rutin v tomto okamžiku, protože aplikace by musela procházet celý seznam. Pokud váš scénář aplikace nikdy nemění <xref:System.Windows.Media.SolidColorBrush>, platíte náklady na údržbu <xref:System.Windows.Freezable.Changed> obslužných rutin událostí zbytečně.  
  
 Zmrazení <xref:System.Windows.Freezable> může zlepšit jeho výkon, protože už nepotřebuje vysílat prostředky na údržbu oznámení změn. Následující tabulka ukazuje velikost jednoduchého <xref:System.Windows.Media.SolidColorBrush>, pokud je jeho vlastnost <xref:System.Windows.Freezable.IsFrozen%2A> nastavena na `true`, ve srovnání s tím, že není. Předpokládá se použití jednoho štětce na vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A> deseti objektů <xref:System.Windows.Shapes.Rectangle>.  
  
|**Stav**|**Velikost**|  
|---------------|--------------|  
|Zmrazený <xref:System.Windows.Media.SolidColorBrush>|212 bajtů|  
|Nezmrazený <xref:System.Windows.Media.SolidColorBrush>|972 bajtů|  
  
 Následující ukázka kódu demonstruje tento koncept:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Změněné obslužné rutiny u nezmrazených Zablokovatelné můžou zachovat objekty v aktivním stavu.  
 Delegát, který objekt předává události <xref:System.Windows.Freezable.Changed> objektu <xref:System.Windows.Freezable>, je efektivně odkaz na tento objekt. Proto obslužné rutiny událostí <xref:System.Windows.Freezable.Changed> můžou zachovat objekty po delší dobu, než se čekalo. Při provádění vyčištění objektu, který je zaregistrován pro naslouchání události <xref:System.Windows.Freezable.Changed> objektu <xref:System.Windows.Freezable>, je nezbytné před uvolněním objektu odebrat tohoto delegáta.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také zapojovat <xref:System.Windows.Freezable.Changed> události interně. Například všechny vlastnosti závislosti, které přijímají <xref:System.Windows.Freezable> jako hodnota, budou automaticky naslouchat událostem <xref:System.Windows.Freezable.Changed>. Tento koncept znázorňuje vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A>, která přebírá <xref:System.Windows.Media.Brush>.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 V případě přiřazení `myBrush` k `myRectangle.Fill`se delegát ukazující zpátky na objekt <xref:System.Windows.Shapes.Rectangle> přidá do události <xref:System.Windows.Freezable.Changed> objektu <xref:System.Windows.Media.SolidColorBrush>. To znamená, že následující kód ve skutečnosti nevede `myRect` způsobil pro uvolňování paměti:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 V tomto případě `myBrush` stále udržuje `myRectangle` Alive a při spuštění události <xref:System.Windows.Freezable.Changed> se do něj vrátí. Všimněte si, že přiřazení `myBrush` k vlastnosti <xref:System.Windows.Shapes.Shape.Fill%2A> nového <xref:System.Windows.Shapes.Rectangle> jednoduše přidá další obslužnou rutinu události do `myBrush`.  
  
 Doporučeným způsobem, jak tyto typy objektů vyčistit, je odebrat <xref:System.Windows.Media.Brush> z vlastnosti <xref:System.Windows.Shapes.Shape.Fill%2A>, která zase odstraní obslužnou rutinu události <xref:System.Windows.Freezable.Changed>.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje variaci prvku <xref:System.Windows.Controls.StackPanel>, který automaticky "virtualizuje" podřízený obsah vázaný na data. V tomto kontextu slovo Virtualization odkazuje na techniku, podle které je vygenerována podmnožina objektů z většího počtu datových položek na základě toho, které položky jsou viditelné na obrazovce. Je náročné, a to jak z paměti, tak i procesoru, aby vygeneroval velký počet prvků uživatelského rozhraní, když na obrazovce v daném okamžiku může být jenom pár. <xref:System.Windows.Controls.VirtualizingStackPanel> (prostřednictvím funkcí poskytovaných <xref:System.Windows.Controls.VirtualizingPanel>) vypočítá viditelné položky a spolupracuje s <xref:System.Windows.Controls.ItemContainerGenerator> od <xref:System.Windows.Controls.ItemsControl> (například <xref:System.Windows.Controls.ListBox> nebo <xref:System.Windows.Controls.ListView>), aby bylo možné vytvářet pouze prvky pro viditelné položky.  
  
 V rámci optimalizace výkonu jsou vizuální objekty pro tyto položky vygenerovány nebo udržovány pouze v případě, že jsou viditelné na obrazovce. Pokud již nejsou v zobrazitelné oblasti ovládacího prvku, může dojít k odebrání vizuálních objektů. Nemusíte se zaměňovat s virtualizací dat, kde datové objekty nejsou v místní kolekci přítomné, a to místo streamování v případě potřeby.  
  
 Následující tabulka ukazuje uplynulý čas přidávání a vykreslování 5000 <xref:System.Windows.Controls.TextBlock> prvků do <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.VirtualizingStackPanel>. V tomto scénáři měření reprezentují čas mezi připojením textového řetězce k vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> objektu <xref:System.Windows.Controls.ItemsControl> až do doby, kdy prvky panelu zobrazují textový řetězec.  
  
|**Panel hostitele**|**Čas vykreslování (MS)**|  
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
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
