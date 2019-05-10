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
ms.openlocfilehash: 9757a8c8327feb40018387473b479e467149f0ed
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611889"
---
# <a name="optimizing-performance-other-recommendations"></a>Optimalizace výkonu: Další doporučení
<a name="introduction"></a> Toto téma obsahuje doporučení k výkonu kromě těch, které jsou předmětem témata v [optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md) oddílu.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Míra průhlednosti na štětce a krytí u elementů](#Opacity)  
  
- [Navigace na objekt](#Navigation_Objects)  
  
- [Testování na velké 3D površích průchodu](#Hit_Testing)  
  
- [CompositionTarget.Rendering události](#CompositionTarget_Rendering_Event)  
  
- [Vyhněte se použití scrollbarvisibility – = Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [Konfigurace služby mezipaměti písma zkrátit čas spuštění](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Míra průhlednosti na štětce a krytí u elementů  
 Při použití <xref:System.Windows.Media.Brush> nastavit <xref:System.Windows.Shapes.Shape.Fill%2A> nebo <xref:System.Windows.Shapes.Shape.Stroke%2A> elementu, je lepší provést nastavení <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> hodnotu místo nastavení prvku <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Změna elementu <xref:System.Windows.UIElement.Opacity%2A> může způsobit, že vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k vytvoření dočasného povrchu.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Navigace na objekt  
 <xref:System.Windows.Navigation.NavigationWindow> Je odvozena z objektu <xref:System.Windows.Window> a rozšiřuje podporující navigaci v obsahu, především na základě agregace <xref:System.Windows.Navigation.NavigationService> a deníku. Můžete aktualizovat klientské oblasti <xref:System.Windows.Navigation.NavigationWindow> zadáním buď [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] nebo objekt. Následující příklad ukazuje obě metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Každý <xref:System.Windows.Navigation.NavigationWindow> objekt má deníku, které zaznamenává historii navigace uživatele v tomto okně. Jedním z účely deník je umožnit uživatelům vrátit jejich kroky.  
  
 Při navigaci pomocí [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], pouze ukládá tento deník [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odkaz. To znamená, že pokaždé, když navštívíte stránku, to je dynamicky znovu vytvořena, což může být časově náročné záleží na složitosti stránky. V takovém případě je nízké náklady na úložiště deníku, ale doba k rekonstrukci stránky je potenciálně vysoká.  
  
 Při navigaci pomocí objektu ukládá tento deník celý vizuální strom objektu. To znamená, že pokaždé, když navštívíte stránku, vykreslí okamžitě bez nutnosti znovu vytvořena. V takovém případě je vysoké náklady na úložiště deníku, ale čas k rekonstrukci stránky je nízká.  
  
 Při použití <xref:System.Windows.Navigation.NavigationWindow> objektu, je potřeba vzít v úvahu, jak podporu záznamu do deníku ovlivňuje výkon vaší aplikace. Další informace najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Testování na velké 3D površích průchodu  
 Přístupů testování na velké 3D ploch velmi výkonu operace je náročná na z hlediska spotřeby procesoru. To platí zejména při animace 3D ploše. Pokud nechcete, aby testování přístupů na tyto tři, pak zakážete přístupů testování. Objekty, které jsou odvozeny z <xref:System.Windows.UIElement> můžete zakázat testování průchodu tak, že nastavíte <xref:System.Windows.UIElement.IsHitTestVisible%2A> vlastnost `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>CompositionTarget.Rendering události  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> Událost způsobí, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] průběžně animovat. Pokud použijete tuto událost, můžete ho odpojte při každé příležitosti.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Vyhněte se použití scrollbarvisibility – = Auto  
 Kdykoli je to možné, vyhněte se použití <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> hodnota `HorizontalScrollBarVisibility` a `VerticalScrollBarVisibility` vlastnosti. Tyto vlastnosti jsou definovány pro <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, a <xref:System.Windows.Controls.TextBox> objekty a jako připojené vlastnosti pro <xref:System.Windows.Controls.ListBox> objektu. Místo toho nastavte <xref:System.Windows.Controls.ScrollBarVisibility> k <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, nebo <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> Hodnota je určena pro případy, když kapacita je omezená a posuvníky má být zobrazena pouze v případě potřeby. Například může být vhodné použít toto <xref:System.Windows.Controls.ScrollBarVisibility> hodnotu <xref:System.Windows.Controls.ListBox> 30 položek, nikoli <xref:System.Windows.Controls.TextBox> spolu se stovkami řádků textu.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Konfigurace služby mezipaměti písma zkrátit čas spuštění  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Písmo Cache service sdílí data písma mezi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací. První [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spustíte aplikaci spustí tuto službu, pokud služba není spuštěná. Pokud používáte [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], "Windows Presentation Foundation (WPF) písmo 3.0.0.0" Služba mezipaměti můžete nastavit od "Ruční" (výchozí) na "Automatické (zpoždění spuštění)" snížit čas spuštění počáteční [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací.  
  
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
