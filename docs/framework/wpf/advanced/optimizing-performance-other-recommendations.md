---
title: 'Optimalizace výkonu: Další doporučení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186305"
---
# <a name="optimizing-performance-other-recommendations"></a>Optimalizace výkonu: Další doporučení
<a name="introduction"></a>Toto téma obsahuje doporučení k výkonu kromě doporučení, která jsou zahrnuta v tématech v části [Optimalizace výkonu aplikací WPF.](optimizing-wpf-application-performance.md)  
  
 Toto téma obsahuje následující oddíly:  
  
- [Krytí stop versus krytí u prvků](#Opacity)  
  
- [Navigace k objektu](#Navigation_Objects)  
  
- [Testování přístupů na velkých 3D površích](#Hit_Testing)  
  
- [Událost CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
- [Vyhněte se použití ScrollBarVisibility=Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [Konfigurace služby mezipaměti písem za účelem zkrácení doby spuštění](#FontCache)  
  
<a name="Opacity"></a>
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Krytí stop versus krytí u prvků  
 Při použití <xref:System.Windows.Media.Brush> nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> nebo <xref:System.Windows.Shapes.Shape.Stroke%2A> prvku, je lepší nastavit hodnotu <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> spíše než nastavení <xref:System.Windows.UIElement.Opacity%2A> vlastnosti prvku. Změna <xref:System.Windows.UIElement.Opacity%2A> vlastnosti prvku může [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] způsobit vytvoření dočasného povrchu.  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a>Navigace k objektu  
 Objekt <xref:System.Windows.Navigation.NavigationWindow> je odvozen <xref:System.Windows.Window> a rozšiřuje jej s podporou navigace obsahu, především <xref:System.Windows.Navigation.NavigationService> agregací a deníku. Klientskou oblast můžete <xref:System.Windows.Navigation.NavigationWindow> aktualizovat zadáním jednotného identifikátoru prostředku (URI) nebo objektu. Následující ukázka ukazuje obě metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Každý <xref:System.Windows.Navigation.NavigationWindow> objekt má deník, který zaznamenává historii navigace uživatele v tomto okně. Jedním z účelů deníku je umožnit uživatelům sledovat jejich kroky.  
  
 Při procházení pomocí identifikátoru URI (uniformní identifikátor prostředku), deník ukládá pouze odkaz identifikátor ujednotného prostředku (URI). To znamená, že pokaždé, když znovu stránku, je dynamicky rekonstruována, což může být časově náročné v závislosti na složitosti stránky. V tomto případě je náklady na úložiště deníku nízké, ale čas rekonstituce stránky je potenciálně vysoká.  
  
 Při navigaci pomocí objektu deník ukládá celý vizuální strom objektu. To znamená, že pokaždé, když znovu stránku, vykreslí okamžitě bez nutnosti rekonstruovat. V tomto případě jsou náklady na úložiště deníku vysoké, ale doba rekonstituce stránky je nízká.  
  
 Při použití <xref:System.Windows.Navigation.NavigationWindow> objektu, budete muset mít na paměti, jak do deníku podporu ovlivňuje výkon vaší aplikace. Další informace naleznete v tématu [Navigační přehled](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a>Testování přístupů na velkých 3D površích  
 Testování přístupů na velkých 3D površích je velmi výkonně náročný provoz z hlediska spotřeby procesoru. To platí zejména při animaci 3D povrchu. Pokud nepotřebujete testování přístupů na těchto površích, zakažte testování přístupů. Objekty, které <xref:System.Windows.UIElement> jsou odvozeny z <xref:System.Windows.UIElement.IsHitTestVisible%2A> můžete `false`zakázat testování přístupů nastavením vlastnosti na .  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a>Událost CompositionTarget.Rendering  
 Událost <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> způsobí, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] že neustále animovat. Pokud použijete tuto událost, odpojte ji při každé příležitosti.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a>Vyhněte se použití ScrollBarVisibility=Auto  
 Kdykoli je to <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> možné, `HorizontalScrollBarVisibility` nepoužívejte hodnotu vlastností a. `VerticalScrollBarVisibility` Tyto vlastnosti <xref:System.Windows.Controls.RichTextBox>jsou <xref:System.Windows.Controls.ScrollViewer>definovány pro , a <xref:System.Windows.Controls.TextBox> objekty <xref:System.Windows.Controls.ListBox> a jako připojená vlastnost objektu. Místo toho <xref:System.Windows.Controls.ScrollBarVisibility> <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>nastavte <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>na <xref:System.Windows.Controls.ScrollBarVisibility.Visible>, , nebo .  
  
 Hodnota <xref:System.Windows.Controls.ScrollBarVisibility.Auto> je určena pro případy, kdy je omezený prostor a posuvníky by měly být zobrazeny pouze v případě potřeby. Například může být užitečné použít <xref:System.Windows.Controls.ScrollBarVisibility> tuto <xref:System.Windows.Controls.ListBox> hodnotu s 30 položek <xref:System.Windows.Controls.TextBox> na rozdíl od a se stovkami řádků textu.  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Konfigurace služby mezipaměti písem za účelem zkrácení doby spuštění  
 Služba WPF Font Cache sdílí data písma mezi aplikacemi WPF. První aplikace WPF, kterou spustíte, spustí tuto službu, pokud služba ještě není spuštěna. Používáte-li systém Windows Vista, můžete z režimu "Ruční" (výchozí) na "Automatické (zpožděné spuštění)" nastavit službu Windows Presentation Foundation (WPF) Font Cache 3.0.0.0 z "Ruční" (výchozí) na "Automatické (zpožděné spuštění)" a zkrátit tak počáteční dobu spuštění aplikací WPF.  
  
## <a name="see-also"></a>Viz také

- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
