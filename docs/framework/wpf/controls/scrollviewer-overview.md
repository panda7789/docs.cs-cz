---
title: ScrollViewer – přehled
description: Přečtěte si o ovládacím prvku ScrollViewer, který umožňuje posouvání obsahu v aplikacích Windows Presentation Foundation. Podívejte se na příklady použití.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 1ef680bb004315a2b523814714d5533535d044e5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164634"
---
# <a name="scrollviewer-overview"></a>ScrollViewer – přehled
Obsah v uživatelském rozhraní je často větší než zobrazovaná oblast obrazovky počítače. <xref:System.Windows.Controls.ScrollViewer>Ovládací prvek poskytuje pohodlný způsob, jak povolit posouvání obsahu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacích. Toto téma představuje <xref:System.Windows.Controls.ScrollViewer> prvek a obsahuje několik příkladů použití.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>Ovládací prvek ScrollViewer  
 Existují dva předdefinované prvky, které umožňují posouvání v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacích: <xref:System.Windows.Controls.Primitives.ScrollBar> a <xref:System.Windows.Controls.ScrollViewer> . <xref:System.Windows.Controls.ScrollViewer>Ovládací prvek zapouzdřuje vodorovné a svislé <xref:System.Windows.Controls.Primitives.ScrollBar> prvky a kontejner obsahu (například <xref:System.Windows.Controls.Panel> element), aby se zobrazily další viditelné prvky v rolovací oblasti. Je nutné vytvořit vlastní objekt, aby bylo možné použít <xref:System.Windows.Controls.Primitives.ScrollBar> element pro posouvání obsahu. Můžete však použít <xref:System.Windows.Controls.ScrollViewer> prvek sám o sobě, protože se jedná o složený ovládací prvek, který zapouzdřuje <xref:System.Windows.Controls.Primitives.ScrollBar> funkce.  
  
 <xref:System.Windows.Controls.ScrollViewer>Ovládací prvek reaguje na příkazy myši i klávesnicí a definuje spoustu metod, pomocí kterých se posune obsah podle předem stanovených přírůstků. Událost můžete použít <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> ke zjištění změny <xref:System.Windows.Controls.ScrollViewer> stavu.  
  
 <xref:System.Windows.Controls.ScrollViewer>Může mít pouze jednu podřízenou položku, obvykle <xref:System.Windows.Controls.Panel> prvek, který může hostovat <xref:System.Windows.Controls.Panel.Children%2A> kolekci prvků. <xref:System.Windows.Controls.ContentPresenter.Content%2A>Vlastnost definuje jediný podřízený objekt <xref:System.Windows.Controls.ScrollViewer> .  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Fyzické a logické posouvání  
 K posouvání obsahu pomocí předem určené fyzického přírůstku se používá fyzické posouvání, obvykle hodnotou, která je deklarována v pixelech. K procházení další položky v logickém stromu se používá logické posouvání. Fyzické posouvání je výchozí chování posouvání pro většinu <xref:System.Windows.Controls.Panel> prvků. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje oba typy posouvání.  
  
#### <a name="the-iscrollinfo-interface"></a>Rozhraní IScrollInfo  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>Rozhraní představuje hlavní oblast posouvání v rámci <xref:System.Windows.Controls.ScrollViewer> nebo odvozeném ovládacím prvku. Rozhraní definuje vlastnosti posouvání a metody, které mohou být implementovány pomocí <xref:System.Windows.Controls.Panel> prvků, které vyžadují posouvání logickou jednotkou, nikoli fyzického zvýšení. Přetypování instance <xref:System.Windows.Controls.Primitives.IScrollInfo> na odvozenou <xref:System.Windows.Controls.Panel> a následným použitím metod posouvání poskytuje užitečný způsob, jak přejít k další logické jednotce v podřízené kolekci, nikoli po zvýšení hodnoty v pixelech. Ve výchozím nastavení <xref:System.Windows.Controls.ScrollViewer> podporuje ovládací prvek posouvání fyzickými jednotkami.  
  
 <xref:System.Windows.Controls.StackPanel>a <xref:System.Windows.Controls.VirtualizingStackPanel> zároveň implementují <xref:System.Windows.Controls.Primitives.IScrollInfo> i nativně podporují logické posouvání. Pro ovládací prvky rozložení, které nativně podporují logické posouvání, můžete stále dosáhnout fyzického posouvání zabalením <xref:System.Windows.Controls.Panel> elementu hostitele v <xref:System.Windows.Controls.ScrollViewer> a nastavením <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> vlastnosti na `false` .  
  
 Následující příklad kódu ukazuje, jak přetypovat instanci <xref:System.Windows.Controls.Primitives.IScrollInfo> na <xref:System.Windows.Controls.StackPanel> a použít metody posouvání obsahu ( <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> ) definované rozhraním.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>Definování a použití elementu ScrollViewer  
 Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> v okně, které obsahuje nějaký text a obdélník. <xref:System.Windows.Controls.Primitives.ScrollBar>prvky se zobrazí pouze v případě potřeby. Při změně velikosti okna se <xref:System.Windows.Controls.Primitives.ScrollBar> prvky zobrazí a zmizí z důvodu aktualizovaných hodnot <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> vlastností a.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>Stylování ScrollViewer  
 Stejně jako všechny ovládací prvky v Windows Presentation Foundation lze styl upravit tak, aby bylo možné <xref:System.Windows.Controls.ScrollViewer> změnit výchozí chování vykreslování ovládacího prvku. Další informace o stylech ovládacích prvků naleznete v tématu [stylování and šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Stránkování dokumentů  
 V případě obsahu dokumentu alternativou k posouvání je výběr kontejneru dokumentů, který podporuje stránkování. <xref:System.Windows.Documents.FlowDocument>je pro dokumenty, které jsou určeny pro hostování v rámci ovládacího prvku pro zobrazení, jako je například <xref:System.Windows.Controls.FlowDocumentPageViewer> , který podporuje stránkování obsahu na více stránkách, což brání nutnosti posouvání. <xref:System.Windows.Controls.DocumentViewer>poskytuje řešení pro zobrazení <xref:System.Windows.Documents.FixedDocument> obsahu, které používá tradiční posouvání k zobrazení obsahu mimo sféru zobrazované oblasti.  
  
 Další informace o formátech dokumentů a možnostech prezentace najdete v tématu [dokumenty v WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Postupy: vytvoření prohlížeče s posuvným zobrazením](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Dokumenty v platformě WPF](../advanced/documents-in-wpf.md)
- [ScrollBar – styly a šablony](scrollbar-styles-and-templates.md)
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
