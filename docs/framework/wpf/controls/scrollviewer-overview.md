---
title: "ScrollViewer – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7317bade85641d7d055facabcf7103b945609583
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="scrollviewer-overview"></a>ScrollViewer – přehled
Často je větší než oblasti obrazovky počítače zobrazení obsahu v uživatelském rozhraní. <xref:System.Windows.Controls.ScrollViewer> Řízení nabízí pohodlný způsob, jak povolit posouvání obsahu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace. Toto téma představuje <xref:System.Windows.Controls.ScrollViewer> elementu a poskytuje několik příkladů použití.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Ovládací prvek ScrollViewer  
 Existují dva předdefinované elementy, které umožňují posouvání v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace: <xref:System.Windows.Controls.Primitives.ScrollBar> a <xref:System.Windows.Controls.ScrollViewer>. <xref:System.Windows.Controls.ScrollViewer> Ovládací prvek zapouzdřuje vodorovně a svisle <xref:System.Windows.Controls.Primitives.ScrollBar> elementy a obsahu kontejneru (například <xref:System.Windows.Controls.Panel> element) aby bylo možné zobrazit další prvky viditelné v posouvatelného oblasti. Chcete-li použít musíte sestavit vlastní objekt <xref:System.Windows.Controls.Primitives.ScrollBar> element pro posouvání obsahu. Můžete však použít <xref:System.Windows.Controls.ScrollViewer> element samostatně, protože je složené řídit, která zapouzdřuje <xref:System.Windows.Controls.Primitives.ScrollBar> funkce.  
  
 <xref:System.Windows.Controls.ScrollViewer> Řízení reaguje na příkazy myši a klávesnice a definuje množství metody, které má být posuňte obsah se po předem určenou přírůstcích. Můžete použít <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> událostí ke zjištění změnu <xref:System.Windows.Controls.ScrollViewer> stavu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> může mít pouze jednu podřízenou, obvykle <xref:System.Windows.Controls.Panel> element, který může hostovat <xref:System.Windows.Controls.Panel.Children%2A> kolekci elementů. <xref:System.Windows.Controls.ContentPresenter.Content%2A> Vlastnost definuje jedinou podřízeným <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Fyzické vs. Logické posouvání  
 Fyzické posouvání slouží posouvat obsah o předem určený fyzické krok obvykle hodnotu, která je deklarován v pixelech. Logické posouvání se používá k přesunutí na další položku v logickém stromu. Fyzické posouvání je výchozí chování posuv pro většinu <xref:System.Windows.Controls.Panel> elementy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podporuje oba typy posouvání.  
  
#### <a name="the-iscrollinfo-interface"></a>Rozhraní IScrollInfo  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> Rozhraní představuje hlavní posouvání oblast v rámci <xref:System.Windows.Controls.ScrollViewer> nebo odvozené ovládací prvek. Definuje rozhraní posouvání vlastnosti a metody, které může být implementována <xref:System.Windows.Controls.Panel> elementy, které vyžadují posouvání logické jednotky, nikoli fyzické přírůstku. Přetypování instanci <xref:System.Windows.Controls.Primitives.IScrollInfo> pro odvozený <xref:System.Windows.Controls.Panel> a pak jeho metodami posouvání poskytuje vhodný způsob, jak přejděte k další logické jednotky v podřízené kolekce, nikoli přírůstek pixelů. Ve výchozím nastavení <xref:System.Windows.Controls.ScrollViewer> řízení podporuje posouvání ve fyzické jednotky.  
  
 <xref:System.Windows.Controls.StackPanel>a <xref:System.Windows.Controls.VirtualizingStackPanel> obě implementovat <xref:System.Windows.Controls.Primitives.IScrollInfo> a nativně podporují logické posouvání. Pro rozložení určuje, že nativně podporu logické posouvání, můžete stále dosáhnout fyzické posouvání nástrojem pro zabalení hostitele <xref:System.Windows.Controls.Panel> element v <xref:System.Windows.Controls.ScrollViewer> a nastavení <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> vlastnost `false`.  
  
 Následující příklad kódu ukazuje, jak převést instanci <xref:System.Windows.Controls.Primitives.IScrollInfo> k <xref:System.Windows.Controls.StackPanel> a použít obsahu posouvání metody (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> a <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) definované rozhraní.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definování a pomocí ScrollViewer elementu.  
 Následující příklad vytvoří <xref:System.Windows.Controls.ScrollViewer> v okně, které obsahuje část textu a obdélníku. <xref:System.Windows.Controls.Primitives.ScrollBar>prvky se zobrazí, jenom když jsou zapotřebí. Když změníte velikost okna, <xref:System.Windows.Controls.Primitives.ScrollBar> prvky zobrazí a zmizí z důvodu aktualizované hodnoty <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> a <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> vlastnosti.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Práce se styly ScrollViewer  
 Stejně jako všechny ovládací prvky v systému Windows Presentation Foundation <xref:System.Windows.Controls.ScrollViewer> můžete navržen tak, aby bylo možné změnit výchozí chování vykreslování ovládacího prvku. Další informace o řízení stylů, najdete v části [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Přestránkování dokumentů  
 Pro obsah dokumentu je alternativa k procházení vyberte kontejner dokumentu, který podporuje stránkování. <xref:System.Windows.Documents.FlowDocument>je pro dokumenty, které mají být hostované v rámci ovládacího prvku zobrazení, jako je například <xref:System.Windows.Controls.FlowDocumentPageViewer>, podporující přestránkování obsah na více stránkách, brání potřebu posouvání. <xref:System.Windows.Controls.DocumentViewer>nabízí řešení pro zobrazení <xref:System.Windows.Documents.FixedDocument> obsah, který používá tradiční posouvání pro zobrazení obsahu mimo sféru oblasti zobrazení.  
  
 Další informace o formátech dokumentu a možnosti prezentace najdete v tématu [dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Vytvoření prohlížeče přejděte](http://msdn.microsoft.com/library/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar – styly a šablony](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [Ovládací prvky](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
