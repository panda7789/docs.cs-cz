---
title: 'Postupy: Práce se sloupci a řádky pomocí objektů ColumnDefinitionsCollections a RowDefinitionsCollections'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
ms.openlocfilehash: 6ff5ad4825bd9f683d895341dd084c00f68aa27b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Postupy: Práce se sloupci a řádky pomocí objektů ColumnDefinitionsCollections a RowDefinitionsCollections
Tento příklad ukazuje, jak používat metody v <xref:System.Windows.Controls.ColumnDefinitionCollection> a <xref:System.Windows.Controls.RowDefinitionCollection> třídy k provádění akcí, jako je přidání, vymazání nebo počítání obsah řádků a sloupců. Například můžete <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, nebo <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> položky, které jsou součástí <xref:System.Windows.Controls.ColumnDefinition> nebo <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Windows.Controls.Grid> element s <xref:System.Windows.FrameworkElement.Name%2A> z `grid1`. <xref:System.Windows.Controls.Grid> Obsahuje <xref:System.Windows.Controls.StackPanel> , obsahuje <xref:System.Windows.Controls.Button> elementy, každý řídí metoda jinou kolekci. Když kliknete <xref:System.Windows.Controls.Button>, aktivuje volání metody v souboru kódu na pozadí.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Tento příklad definuje řadu vlastních metod, každý odpovídající <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru. Můžete změnit počet sloupců a řádků v <xref:System.Windows.Controls.Grid> několika způsoby, což zahrnuje přidání nebo odebrání řádků a sloupců; a poté celkový počet řádků a sloupců. Aby se zabránilo <xref:System.ArgumentOutOfRangeException> a <xref:System.ArgumentException> výjimky, můžete použít funkci chyb, <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> poskytuje metoda.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
