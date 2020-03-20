---
title: ScrollViewer – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 2ff0f134ea3174f7f034d47446aab782e2141916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186989"
---
# <a name="scrollviewer-overview"></a>ScrollViewer – přehled
Obsah v uživatelském rozhraní je často větší než oblast zobrazení obrazovky počítače. Ovládací <xref:System.Windows.Controls.ScrollViewer> prvek poskytuje pohodlný způsob, jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] povolit posouvání obsahu v aplikacích. Toto téma <xref:System.Windows.Controls.ScrollViewer> představuje prvek a poskytuje několik příkladů použití.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>Ovládací prvek ScrollViewer  
 Existují dva předdefinované prvky, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] které <xref:System.Windows.Controls.Primitives.ScrollBar> umožňují <xref:System.Windows.Controls.ScrollViewer>posouvání v aplikacích: a . Ovládací <xref:System.Windows.Controls.ScrollViewer> prvek zapouzdřuje vodorovné a svislé <xref:System.Windows.Controls.Primitives.ScrollBar> prvky a kontejner obsahu (například <xref:System.Windows.Controls.Panel> prvek) za účelem zobrazení dalších viditelných prvků v posuvné oblasti. Chcete-li prvek použít <xref:System.Windows.Controls.Primitives.ScrollBar> pro posouvání obsahu, je nutné vytvořit vlastní objekt. <xref:System.Windows.Controls.ScrollViewer> Prvek však můžete použít samostatně, protože se jedná o složený <xref:System.Windows.Controls.Primitives.ScrollBar> ovládací prvek, který zapouzdřuje funkce.  
  
 Ovládací <xref:System.Windows.Controls.ScrollViewer> prvek reaguje na příkazy myši a klávesnice a definuje mnoho metod, pomocí kterých chcete posouvat obsah předem určené přírůstky. <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> Událost můžete použít k detekci <xref:System.Windows.Controls.ScrollViewer> změny ve stavu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> může mít pouze jeden <xref:System.Windows.Controls.Panel> podřízený, obvykle <xref:System.Windows.Controls.Panel.Children%2A> prvek, který může hostit kolekci prvků. Vlastnost <xref:System.Windows.Controls.ContentPresenter.Content%2A> definuje jediný podřízený <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Fyzické vs. logické posouvání  
 Fyzické posouvání se používá k posouvání obsahu předem určeným fyzickým přírůstkem, obvykle hodnotou, která je deklarována v pixelech. Logické posouvání se používá k přechodu na další položku v logickém stromu. Fyzické posouvání je výchozí chování <xref:System.Windows.Controls.Panel> posouvání pro většinu prvků. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje oba typy posouvání.  
  
#### <a name="the-iscrollinfo-interface"></a>Rozhraní iScrollInfo  
 Rozhraní <xref:System.Windows.Controls.Primitives.IScrollInfo> představuje hlavní oblast posouvání <xref:System.Windows.Controls.ScrollViewer> v rámci nebo odvozené ovládací prvek. Rozhraní definuje rolování vlastnosti a metody, <xref:System.Windows.Controls.Panel> které mohou být implementovány prvky, které vyžadují posouvání podle logické jednotky, spíše než fyzický přírůstek. Obsazení instance <xref:System.Windows.Controls.Primitives.IScrollInfo> na odvozené <xref:System.Windows.Controls.Panel> a pak pomocí jeho scrolling metody poskytuje užitečný způsob, jak posunout na další logickou jednotku v podřízené kolekci, nikoli podle přírůstku pixelů. Ve výchozím <xref:System.Windows.Controls.ScrollViewer> nastavení podporuje ovládací prvek posouvání podle fyzických jednotek.  
  
 <xref:System.Windows.Controls.StackPanel>a <xref:System.Windows.Controls.VirtualizingStackPanel> implementovat <xref:System.Windows.Controls.Primitives.IScrollInfo> i nativně podporovat logické posouvání. U ovládacích prvků rozložení, které nativně podporují logické posouvání, <xref:System.Windows.Controls.Panel> můžete <xref:System.Windows.Controls.ScrollViewer> stále dosáhnout <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> fyzického posouvání zabalením prvku hostitele do a nastavením vlastnosti na `false`.  
  
 Následující příklad kódu ukazuje, jak přetypovat instanci <xref:System.Windows.Controls.Primitives.IScrollInfo> <xref:System.Windows.Controls.StackPanel> a<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> používat <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>metody posouvání obsahu ( a ) definované rozhraním.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>Definování a použití prvku ScrollViewer  
 Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> v okně, které obsahuje nějaký text a obdélník. <xref:System.Windows.Controls.Primitives.ScrollBar>prvky se zobrazí pouze v případě, že jsou nezbytné. Při změně velikosti okna <xref:System.Windows.Controls.Primitives.ScrollBar> se prvky zobrazí a zmizí <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> z důvodu aktualizovaných hodnot vlastností a.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>Stylování scrollvieweru  
 Stejně jako všechny ovládací <xref:System.Windows.Controls.ScrollViewer> prvky v systému Windows Presentation Foundation, lze stylizovaný změnit výchozí chování vykreslování ovládacího prvku. Další informace o stylu ovládacího prvku naleznete [v tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Stránkování dokumentů  
 Pro obsah dokumentu je alternativou k posouvání volba kontejneru dokumentu, který podporuje stránkování. <xref:System.Windows.Documents.FlowDocument>je pro dokumenty, které jsou navrženy tak, <xref:System.Windows.Controls.FlowDocumentPageViewer>aby byly hostovány v ovládacím prvku zobrazení, například , který podporuje stránkování obsahu na více stránkách a zabraňuje nutnosti posouvání. <xref:System.Windows.Controls.DocumentViewer>Poskytuje řešení pro <xref:System.Windows.Documents.FixedDocument> zobrazení obsahu, které používá tradiční posouvání k zobrazení obsahu mimo oblast zobrazení.  
  
 Další informace o formátech dokumentů a možnostech prezentace naleznete [v tématu Dokumenty v dokumentu WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Postup: Vytvoření prohlížeče posouvání](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Dokumenty v platformě WPF](../advanced/documents-in-wpf.md)
- [ScrollBar – styly a šablony](scrollbar-styles-and-templates.md)
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
