---
title: "Postupy: Získání posunu vizuálního objektu"
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
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee18503bdd6100cbe7a62ac70d7ea0848fb124eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-the-offset-of-a-visual"></a>Postupy: Získání posunu vizuálního objektu
Tyto příklady ukazují, jak načíst hodnoty posunu visual objektu, která je relativní k jeho nadřazeným prvkem, nebo jakékoli nadřazené nebo následníka.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kód <xref:System.Windows.Controls.TextBlock> který je definován s <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu 4.  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metoda pro načtení posun <xref:System.Windows.Controls.TextBlock>. Hodnoty posunutí jsou obsaženy v rámci vrácený <xref:System.Windows.Vector> hodnotu.  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu. V takovém případě <xref:System.Windows.Vector.X%2A> je 4, a <xref:System.Windows.Vector.Y%2A> je 4.  
  
 Vrácená hodnota posunutí je relativní vzhledem ke nadřazeného <xref:System.Windows.Media.Visual>. Pokud chcete vrátí posunutí hodnotu, která je relativní vzhledem k nadřazeného <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metoda.  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>Získávání posun relativní k nadřazenému prvku  
 Následující příklad ukazuje kód <xref:System.Windows.Controls.TextBlock> který je vnořen do dvou <xref:System.Windows.Controls.StackPanel> objekty.  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 Následující obrázek znázorňuje výsledky kód.  
  
 ![Hodnoty posunutí objektů](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")  
TextBlock vnořených ve dvou StackPanels  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metoda pro načtení posun <xref:System.Windows.Controls.TextBlock> relativně k obsahující <xref:System.Windows.Window>. Hodnoty posunutí jsou obsaženy v rámci vrácený <xref:System.Windows.Media.GeneralTransform> hodnotu.  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty v rámci obsahující <xref:System.Windows.Window>. V takovém případě <xref:System.Windows.Vector.X%2A> je 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> je 28.  
  
 Vrácená hodnota posunutí je relativní vzhledem ke nadřazeného <xref:System.Windows.Media.Visual>. Pokud chcete vrátí posunutí hodnotu, která je relativní vzhledem k následníka <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metoda.  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>Získávání posun vzhledem k následníka  
 Následující příklad ukazuje kód <xref:System.Windows.Controls.TextBlock> obsažená v rámci <xref:System.Windows.Controls.StackPanel> objektu.  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metoda pro načtení posun <xref:System.Windows.Controls.StackPanel> relativně k jeho podřízené <xref:System.Windows.Controls.TextBlock>. Hodnoty posunutí jsou obsaženy v rámci vrácený <xref:System.Windows.Media.GeneralTransform> hodnotu.  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty. V takovém případě <xref:System.Windows.Vector.X%2A> -4, je a <xref:System.Windows.Vector.Y%2A> -4 je. Posunutí hodnoty jsou záporné hodnoty, protože nadřazený objekt je negativní posunuto vzhledem ke své podřízený objekt.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
