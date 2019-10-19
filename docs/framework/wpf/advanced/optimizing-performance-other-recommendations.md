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
ms.openlocfilehash: cf621ab5f423e2465999b26f32489af1132bece0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582454"
---
# <a name="optimizing-performance-other-recommendations"></a>Optimalizace výkonu: Další doporučení
<a name="introduction"></a>Toto téma poskytuje doporučení pro výkon kromě těch, které jsou pokryty v tématech v části [optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md) .  
  
 Toto téma obsahuje následující oddíly:  
  
- [Průhlednost u štětců versus neprůhlednost u elementů](#Opacity)  
  
- [Navigace k objektu](#Navigation_Objects)  
  
- [Testování přístupů na velké 3D povrchy](#Hit_Testing)  
  
- [Událost CompositionTarget. rendering](#CompositionTarget_Rendering_Event)  
  
- [Nepoužívejte ScrollBarVisibility = auto.](#Avoid_Using_ScrollBarVisibility)  
  
- [Nakonfigurujte Cache Service písma, aby se snížil čas spuštění.](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Průhlednost u štětců versus neprůhlednost u elementů  
 Použijete-li <xref:System.Windows.Media.Brush> k nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> nebo <xref:System.Windows.Shapes.Shape.Stroke%2A> prvku, je vhodnější nastavit <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> hodnotu namísto nastavení vlastnosti <xref:System.Windows.UIElement.Opacity%2A> elementu. Změna vlastnosti <xref:System.Windows.UIElement.Opacity%2A> elementu může způsobit, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří dočasnou plochu.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Navigace k objektu  
 Objekt <xref:System.Windows.Navigation.NavigationWindow> je odvozen z <xref:System.Windows.Window> a rozšiřuje ho o podporu navigace obsahu, a to hlavně agregací <xref:System.Windows.Navigation.NavigationService> a deníku. Klientskou oblast <xref:System.Windows.Navigation.NavigationWindow> můžete aktualizovat tak, že zadáte buď identifikátor URI (Uniform Resource Identifier), nebo objekt. Následující příklad ukazuje obě metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Každý objekt <xref:System.Windows.Navigation.NavigationWindow> obsahuje deník, který zaznamenává historii navigace uživatele v tomto okně. Jedním z účelů deníku je dovolit uživatelům přesledovat jejich kroky.  
  
 Při procházení pomocí identifikátoru URI (Uniform Resource Identifier) ukládá deník pouze odkaz na identifikátor URI (Uniform Resource Identifier). To znamená, že pokaždé, když stránku znovu navštívíte, je dynamicky znovu sestavena, což může být časově náročné v závislosti na složitosti stránky. V tomto případě jsou náklady na úložiště deníku nízké, ale čas, který je potřeba znovu vytvořit stránku, je potenciálně vysoký.  
  
 Při procházení pomocí objektu deník ukládá celý vizuální strom objektu. To znamená, že pokaždé, když stránku znovu navštívíte, vykreslí se okamžitě, aniž by bylo nutné je znovu sestavit. V tomto případě jsou náklady na úložiště deníku vysoké, ale čas, který se má znovu zakládat, je nízký.  
  
 Při použití objektu <xref:System.Windows.Navigation.NavigationWindow> budete muset pamatovat na to, jak zařadí podpora do deníku vliv na výkon vaší aplikace. Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Testování přístupů na velké 3D povrchy  
 Testování přístupů na velké trojrozměrné povrchy je velmi náročná operace s ohledem na využití procesoru. To platí hlavně při animování prostorového povrchu. Pokud pro tyto povrchy nepožadujete testování přístupů, zakažte testování přístupů. Objekty odvozené z <xref:System.Windows.UIElement> mohou zakázat testování přístupů nastavením vlastnosti <xref:System.Windows.UIElement.IsHitTestVisible%2A> na `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Událost CompositionTarget. rendering  
 Událost <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> způsobuje nepřetržitou animaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pokud použijete tuto událost, odpojte ji při každé příležitosti.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Nepoužívejte ScrollBarVisibility = auto.  
 Kdykoli je to možné, vyhněte se použití <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> hodnoty vlastností `HorizontalScrollBarVisibility` a `VerticalScrollBarVisibility`. Tyto vlastnosti jsou definovány pro objekty <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer> a <xref:System.Windows.Controls.TextBox> a jako připojená vlastnost pro objekt <xref:System.Windows.Controls.ListBox>. Místo toho nastavte <xref:System.Windows.Controls.ScrollBarVisibility> na <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden> nebo <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 Hodnota <xref:System.Windows.Controls.ScrollBarVisibility.Auto> je určena pro případy, kdy je omezen prostor, a v případě potřeby by se měly zobrazovat posuvníky. Může být například užitečné použít tuto <xref:System.Windows.Controls.ScrollBarVisibility> hodnotu s <xref:System.Windows.Controls.ListBox> 30 položek na rozdíl od <xref:System.Windows.Controls.TextBox> se stovkami řádků textu.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Nakonfigurujte Cache Service písma, aby se snížil čas spuštění.  
 Služba mezipaměť písem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sdílí data písma mezi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacemi. První spouštěná aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spustí tuto službu, pokud služba ještě není spuštěná. Pokud používáte [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], můžete nastavit službu mezipaměť písem "Windows Presentation Foundation (WPF) 3.0.0.0" z "Manual" (výchozí) na "automaticky (zpožděné spuštění)", aby se snížila doba počátečního spuštění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací.  
  
## <a name="see-also"></a>Viz také:

- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
