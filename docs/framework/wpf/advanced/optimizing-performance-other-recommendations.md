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
ms.openlocfilehash: 3ea776dcb1b8633922aafca31821d367a11260f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-other-recommendations"></a>Optimalizace výkonu: Další doporučení
<a name="introduction"></a> Toto téma obsahuje doporučení výkonu kromě těch, které jsou předmětem témata v [optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md) části.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Krytí na štětce Versus krytí u elementů](#Opacity)  
  
-   [Navigace k objektu](#Navigation_Objects)  
  
-   [Testování na velké 3D plochy průchodu](#Hit_Testing)  
  
-   [CompositionTarget.Rendering událostí](#CompositionTarget_Rendering_Event)  
  
-   [Nepoužívejte ScrollBarVisibility = Auto](#Avoid_Using_ScrollBarVisibility)  
  
-   [Konfigurace služby mezipaměti písma pro zkrácení doby spouštění](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Krytí na štětce Versus krytí u elementů  
 Při použití <xref:System.Windows.Media.Brush> nastavit <xref:System.Windows.Shapes.Shape.Fill%2A> nebo <xref:System.Windows.Shapes.Shape.Stroke%2A> elementu, je lepší nastavit <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> hodnotu místo nastavení elementu <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Úprava elementu <xref:System.Windows.UIElement.Opacity%2A> vlastnost může způsobit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořit dočasný prostor.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Navigace k objektu  
 <xref:System.Windows.Navigation.NavigationWindow> Objektu je odvozena z <xref:System.Windows.Window> a rozšiřuje podporu obsahu navigace, především podle agregování <xref:System.Windows.Navigation.NavigationService> a deníku. Klientské oblasti můžete aktualizovat <xref:System.Windows.Navigation.NavigationWindow> zadáním buď [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] nebo objekt. Následující příklad ukazuje obě metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Každý <xref:System.Windows.Navigation.NavigationWindow> objekt má deník, který zaznamenává historii navigace uživatele v okně. Jeden z účely deník je povolit uživatelům-li se vrátit jejich kroky.  
  
 Když přejdete pomocí [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], deník ukládá jenom [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz. To znamená, že pokaždé, když otevírat stránku, ho je dynamicky znovu vytvořena, což může být časově náročná v závislosti na složitosti stránky. V takovém případě je nízké náklady na úložiště deníku, ale čas potřebný k-rekonstruovat stránky je potenciálně vysoká.  
  
 Když přejdete pomocí objektu, ukládá deník celý strom visual objektu. To znamená, že pokaždé, když otevírat stránku, vykreslí okamžitě bez nutnosti znovu vytvořena. V takovém případě náklady na úložiště deníku je vysoká, ale čas potřebný k-rekonstruovat stránky je nízká.  
  
 Při použití <xref:System.Windows.Navigation.NavigationWindow> objekt, je nutné mít na paměti, jak podporu deníku ovlivňuje výkon aplikace. Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Testování na velké 3D plochy průchodu  
 Přístupů testování na velké 3D ploch velmi výkonu operace je náročná na z hlediska spotřeby procesoru. To platí hlavně při 3D prostor je animaci. Pokud nechcete, aby na tyto tři přístupů testování, pak zakažte přístupů testování. Objekty, které jsou odvozeny od <xref:System.Windows.UIElement> můžete zakázat testování průchodu nastavením <xref:System.Windows.UIElement.IsHitTestVisible%2A> vlastnost `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>CompositionTarget.Rendering událostí  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> Události způsobí, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do nepřetržitě animace. Pokud chcete použít tuto událost, odpojte se při každé příležitosti.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Nepoužívejte ScrollBarVisibility = Auto  
 Pokud je to možné, vyhněte se použití <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> hodnota `HorizontalScrollBarVisibility` a `VerticalScrollBarVisibility` vlastnosti. Tyto vlastnosti jsou definovány pro <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, a <xref:System.Windows.Controls.TextBox> objekty a jako přidružená vlastnost pro <xref:System.Windows.Controls.ListBox> objektu. Místo toho nastavte <xref:System.Windows.Controls.ScrollBarVisibility> k <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, nebo <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> Hodnota je určena pro případy, když místo je omezený a posuvníky by měl zobrazí jenom v případě potřeby. Například může být užitečné používat <xref:System.Windows.Controls.ScrollBarVisibility> hodnotu s <xref:System.Windows.Controls.ListBox> 30 položek naproti tomu <xref:System.Windows.Controls.TextBox> se stovkami řádků textu.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Konfigurace služby mezipaměti písma pro zkrácení doby spouštění  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Písma mezipaměti služba sdílí písma dat mezi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace. První [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikaci spustíte spustí tuto službu, pokud ještě není spuštěná služba. Pokud používáte [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], můžete nastavit službu "Windows Presentation Foundation (WPF) písma mezipaměť 3.0.0.0" z "Ruční" (výchozí) automatická, (opožděná Start) snížit čas spuštění počáteční [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Chování objektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Tipy a triky animace](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
