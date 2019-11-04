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
ms.openlocfilehash: 993f3c861cbead88df3503eb01f18e5d1f69e2d8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458432"
---
# <a name="scrollviewer-overview"></a>ScrollViewer – přehled
Obsah v uživatelském rozhraní je často větší než zobrazovaná oblast obrazovky počítače. Ovládací prvek <xref:System.Windows.Controls.ScrollViewer> poskytuje pohodlný způsob, jak povolit posouvání obsahu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacích. Toto téma představuje prvek <xref:System.Windows.Controls.ScrollViewer> a obsahuje několik příkladů použití.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Ovládací prvek ScrollViewer  
 Existují dva předdefinované prvky, které umožňují posouvání v aplikacích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: <xref:System.Windows.Controls.Primitives.ScrollBar> a <xref:System.Windows.Controls.ScrollViewer>. Ovládací prvek <xref:System.Windows.Controls.ScrollViewer> zapouzdřuje vodorovné a svislé prvky <xref:System.Windows.Controls.Primitives.ScrollBar> a kontejner obsahu (například prvek <xref:System.Windows.Controls.Panel>), aby bylo možné zobrazit další viditelné prvky v rolovací oblasti. Je nutné vytvořit vlastní objekt, aby bylo možné použít prvek <xref:System.Windows.Controls.Primitives.ScrollBar> pro posouvání obsahu. Můžete však použít prvek <xref:System.Windows.Controls.ScrollViewer> sám o sobě, protože se jedná o složený ovládací prvek, který zapouzdřuje funkce <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 Ovládací prvek <xref:System.Windows.Controls.ScrollViewer> reaguje na příkazy myši a klávesnicí a definuje spoustu metod, pomocí kterých se má posunovat obsah podle předem stanovených přírůstků. Můžete použít událost <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> k detekci změny ve stavu <xref:System.Windows.Controls.ScrollViewer>.  
  
 <xref:System.Windows.Controls.ScrollViewer> může mít pouze jednu podřízenou položku, obvykle <xref:System.Windows.Controls.Panel> prvek, který může hostovat <xref:System.Windows.Controls.Panel.Children%2A> kolekci prvků. Vlastnost <xref:System.Windows.Controls.ContentPresenter.Content%2A> definuje výlučnou podřízenou položku <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Fyzické a logické posouvání  
 K posouvání obsahu pomocí předem určené fyzického přírůstku se používá fyzické posouvání, obvykle hodnotou, která je deklarována v pixelech. K procházení další položky v logickém stromu se používá logické posouvání. Fyzické posouvání je výchozí chování posouvání pro většinu <xref:System.Windows.Controls.Panel> prvků. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje oba typy posouvání.  
  
#### <a name="the-iscrollinfo-interface"></a>Rozhraní IScrollInfo  
 Rozhraní <xref:System.Windows.Controls.Primitives.IScrollInfo> představuje hlavní oblast posouvání v rámci <xref:System.Windows.Controls.ScrollViewer> nebo odvozeného ovládacího prvku. Rozhraní definuje vlastnosti posouvání a metody, které mohou být implementovány <xref:System.Windows.Controls.Panel> prvky, které vyžadují posouvání logickou jednotkou, nikoli fyzické zvýšení. Přetypování instance <xref:System.Windows.Controls.Primitives.IScrollInfo> na odvozenou <xref:System.Windows.Controls.Panel> a následné použití metod posouvání poskytuje užitečný způsob, jak přejít k další logické jednotce v podřízené kolekci, nikoli po zvýšení hodnoty v pixelech. Ve výchozím nastavení podporuje ovládací prvek <xref:System.Windows.Controls.ScrollViewer> procházení fyzickými jednotkami.  
  
 <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.VirtualizingStackPanel> implementace <xref:System.Windows.Controls.Primitives.IScrollInfo> i nativně podporují logické posouvání. Pro ovládací prvky rozložení, které nativně podporují logické posouvání, můžete stále dosáhnout fyzického posouvání tím, že zabalíte <xref:System.Windows.Controls.Panel> prvek hostitele v <xref:System.Windows.Controls.ScrollViewer> a nastavíte vlastnost <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> na `false`.  
  
 Následující příklad kódu ukazuje, jak přetypovat instanci <xref:System.Windows.Controls.Primitives.IScrollInfo> na <xref:System.Windows.Controls.StackPanel> a použít metody posouvání obsahu (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) definované rozhraním.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definování a použití elementu ScrollViewer  
 Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> v okně, které obsahuje nějaký text a obdélník. prvky <xref:System.Windows.Controls.Primitives.ScrollBar> se zobrazí pouze v případě potřeby. Při změně velikosti okna se <xref:System.Windows.Controls.Primitives.ScrollBar> prvky zobrazí a zmizí z důvodu aktualizovaných hodnot vlastností <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> a <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Stylování ScrollViewer  
 Stejně jako všechny ovládací prvky v Windows Presentation Foundation lze <xref:System.Windows.Controls.ScrollViewer> stylem změnit, aby bylo možné změnit výchozí chování vykreslování ovládacího prvku. Další informace o stylech ovládacích prvků naleznete v tématu [stylování and šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Stránkování dokumentů  
 V případě obsahu dokumentu alternativou k posouvání je výběr kontejneru dokumentů, který podporuje stránkování. <xref:System.Windows.Documents.FlowDocument> je pro dokumenty, které jsou určené k hostování v rámci ovládacího prvku pro zobrazení, jako je například <xref:System.Windows.Controls.FlowDocumentPageViewer>, který podporuje stránkování obsahu na více stránkách, což brání nutnosti posouvání. <xref:System.Windows.Controls.DocumentViewer> poskytuje řešení pro zobrazování obsahu <xref:System.Windows.Documents.FixedDocument>, který používá tradiční posouvání k zobrazení obsahu mimo sféru zobrazované oblasti.  
  
 Další informace o formátech dokumentů a možnostech prezentace najdete v tématu [dokumenty v WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Postupy: vytvoření prohlížeče s posuvným zobrazením](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Dokumenty v platformě WPF](../advanced/documents-in-wpf.md)
- [ScrollBar – styly a šablony](scrollbar-styles-and-templates.md)
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
