---
title: 'Postupy: Získání posunu vizuálního objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093407"
---
# <a name="how-to-get-the-offset-of-a-visual"></a>Postupy: Získání posunu vizuálního objektu
Tyto příklady znázorňují postup načtení hodnoty posunu vizuální objekt, který je relativní vůči nadřazeného objektu, nebo všechny nadřazený sobě samé.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje značky <xref:System.Windows.Controls.TextBlock> , která je definována s <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu 4.  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metodu pro načtení posun <xref:System.Windows.Controls.TextBlock>. Posunutí hodnoty jsou obsaženy v rámci vrácené <xref:System.Windows.Vector> hodnotu.  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnotu. V takovém případě <xref:System.Windows.Vector.X%2A> je 4 a <xref:System.Windows.Vector.Y%2A> je 4.  
  
 Vrácená hodnota posunu je relativní vůči nadřazeného člena <xref:System.Windows.Media.Visual>. Pokud budete chtít vrátit hodnoty posunu, který není relativní vzhledem k nadřazený <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metody.  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>Získání posunu relativní k nadřazenému prvku  
 Následující příklad ukazuje značky <xref:System.Windows.Controls.TextBlock> , která je vnořená v rámci dvou <xref:System.Windows.Controls.StackPanel> objekty.  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 Následující obrázek znázorňuje výsledky značky.  
  
 ![Hodnoty posunutí objektů](./media/visualoffset-01.png "VisualOffset_01")  
Vnořené dvě StackPanels TextBlock  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metodu pro načtení posun <xref:System.Windows.Controls.TextBlock> vzhledem k nadřazeného <xref:System.Windows.Window>. Posunutí hodnoty jsou obsaženy v rámci vrácené <xref:System.Windows.Media.GeneralTransform> hodnotu.  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty v rámci nadřazeného <xref:System.Windows.Window>. V takovém případě <xref:System.Windows.Vector.X%2A> je 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> je 28.  
  
 Vrácená hodnota posunu je relativní vůči nadřazeného člena pro <xref:System.Windows.Media.Visual>. Pokud budete chtít vrátit hodnotu posunu, která je relativní k potomkem <xref:System.Windows.Media.Visual>, použijte <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metody.  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>Získávání posun vzhledem ke potomkem  
 Následující příklad ukazuje značky <xref:System.Windows.Controls.TextBlock> , který je součástí <xref:System.Windows.Controls.StackPanel> objektu.  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metodu pro načtení posun <xref:System.Windows.Controls.StackPanel> vzhledem k jeho dceřiný <xref:System.Windows.Controls.TextBlock>. Posunutí hodnoty jsou obsaženy v rámci vrácené <xref:System.Windows.Media.GeneralTransform> hodnotu.  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 Posun bere v úvahu <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty pro všechny objekty. V takovém případě <xref:System.Windows.Vector.X%2A> se -4, a <xref:System.Windows.Vector.Y%2A> se -4. Hodnoty posunutí jsou záporné hodnoty, protože nadřazený objekt je negativní posun vzhledem k jeho podřízený objekt.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
