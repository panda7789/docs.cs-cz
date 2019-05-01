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
ms.openlocfilehash: a3302d9c360b0918a1fce956af3e3aa14f29361b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024024"
---
# <a name="scrollviewer-overview"></a>ScrollViewer – přehled
Obsah v rámci uživatelského rozhraní je často větší než oblasti zobrazení obrazovce počítače. <xref:System.Windows.Controls.ScrollViewer> Řízení poskytuje pohodlný způsob, jak povolit posouvání obsahu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací. Toto téma představuje <xref:System.Windows.Controls.ScrollViewer> elementu a obsahuje několik příkladů použití.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Scrollviewer – ovládací prvek  
 Existují dvě předdefinované prvky, které umožňují posouvání v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací: <xref:System.Windows.Controls.Primitives.ScrollBar> a <xref:System.Windows.Controls.ScrollViewer>. <xref:System.Windows.Controls.ScrollViewer> Ovládací prvek zapouzdřuje vodorovně a svisle <xref:System.Windows.Controls.Primitives.ScrollBar> prvků a obsahu kontejneru (například <xref:System.Windows.Controls.Panel> element) zobrazíte další viditelné prvky v posuvné oblasti. Chcete-li použít je nutné vytvořit vlastní objekt <xref:System.Windows.Controls.Primitives.ScrollBar> – element pro posouvání obsahu. Můžete však použít <xref:System.Windows.Controls.ScrollViewer> element samostatně, protože se jedná složený ovládací prvek, který zapouzdřuje <xref:System.Windows.Controls.Primitives.ScrollBar> funkce.  
  
 <xref:System.Windows.Controls.ScrollViewer> Ovládací prvek odpovídá na příkazy myš a klávesnici a definuje řadou metod, pomocí kterého se má po předem určenou přírůstcích posouvání obsahu. Můžete použít <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> událostí, aby mohl zjišťovat změny v <xref:System.Windows.Controls.ScrollViewer> stavu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> může mít pouze jeden podřízený prvek, obvykle <xref:System.Windows.Controls.Panel> element, který může hostovat <xref:System.Windows.Controls.Panel.Children%2A> kolekci elementů. <xref:System.Windows.Controls.ContentPresenter.Content%2A> Vlastnost definuje jediným podřízeným <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Fyzické vs. Logické posouvání  
 Fyzické posouvání používá posouvat obsah předem fyzické přírůstek, obvykle podle hodnoty, která je deklarována v pixelech. Logické posouvání se používá k přesunutí na další položku v logickém stromu. Fyzické posouvání je výchozí chování posouvání pro většinu <xref:System.Windows.Controls.Panel> elementy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podporuje oba typy posouvání.  
  
#### <a name="the-iscrollinfo-interface"></a>Iscrollinfo – rozhraní  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> Rozhraní představuje hlavní oblast posouvání v rámci <xref:System.Windows.Controls.ScrollViewer> nebo ovládací prvek odvozený. Definuje rozhraní umožňující posouvání vlastnosti a metody, které může být implementována <xref:System.Windows.Controls.Panel> prvky, které vyžadují posouvání logickou jednotku, nikoli fyzické přírůstku. Přetypování instance <xref:System.Windows.Controls.Primitives.IScrollInfo> pro odvozený <xref:System.Windows.Controls.Panel> a pak pomocí jeho metody posunování poskytuje vhodný způsob, přejděte k další logické jednotky v podřízené kolekce, nikoli v přírůstcích po pixelů. Ve výchozím nastavení <xref:System.Windows.Controls.ScrollViewer> ovládací prvek podporuje posouvání ve fyzické jednotky.  
  
 <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.VirtualizingStackPanel> i implementaci <xref:System.Windows.Controls.Primitives.IScrollInfo> a nativně podporují logické posouvání. Pro rozložení ovládacích prvků tuto nativní podporu logické posouvání, můžete stále dosáhnout fyzické posouvání obalením hostitele <xref:System.Windows.Controls.Panel> prvek <xref:System.Windows.Controls.ScrollViewer> a nastavení <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> vlastnost `false`.  
  
 Následující příklad kódu ukazuje, jak k přetypování instance <xref:System.Windows.Controls.Primitives.IScrollInfo> k <xref:System.Windows.Controls.StackPanel> a použití obsahu umožňující posouvání metod (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) definované rozhraní.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definování a použití prvku ScrollViewer  
 Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> v okně, které obsahuje nějaký text a obdélníku. <xref:System.Windows.Controls.Primitives.ScrollBar> prvky se zobrazí, jenom když nejsou nezbytné. Když změníte velikost okna, <xref:System.Windows.Controls.Primitives.ScrollBar> prvky se zobrazí a zmizí z důvodu aktualizované hodnoty <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> a <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> vlastnosti.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Práce se styly prvku ScrollViewer  
 Ve Windows Presentation Foundation, všechny ovládací prvky, jako jsou <xref:System.Windows.Controls.ScrollViewer> můžete navržen tak, aby bylo možné změnit výchozí chování vykreslování ovládacího prvku. Další informace o určení stylu ovládacího prvku, naleznete v tématu [styly a šablony](styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Stránkování dokumenty  
 Pro obsah dokumentů je alternativou k posouvání vyberte kontejner dokumentu, který podporuje stránkování. <xref:System.Windows.Documents.FlowDocument> je pro dokumenty, které jsou navržené tak zajistit také jejich hostování v rámci ovládacího prvku zobrazení, jako například <xref:System.Windows.Controls.FlowDocumentPageViewer>, podporuje stránkování obsah na několika stránkách brání není nutné. <xref:System.Windows.Controls.DocumentViewer> poskytuje řešení pro zobrazení <xref:System.Windows.Documents.FixedDocument> obsah, který používá tradiční posouvání k zobrazení obsahu mimo sféry oblasti zobrazení.  
  
 Další informace o formátech dokumentu a prezentace možnosti najdete v tématu [dokumenty v platformě WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Postupy: Vytvoření prohlížeče s posuvným zobrazením](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Dokumenty v platformě WPF](../advanced/documents-in-wpf.md)
- [ScrollBar – styly a šablony](scrollbar-styles-and-templates.md)
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
