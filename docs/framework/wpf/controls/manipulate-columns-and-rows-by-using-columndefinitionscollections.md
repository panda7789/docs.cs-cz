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
ms.openlocfilehash: f316cced076223edba1d39c9cfb21b9a504b9eee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978273"
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Postupy: Práce se sloupci a řádky pomocí objektů ColumnDefinitionsCollections a RowDefinitionsCollections
Tento příklad ukazuje způsob použití metody v <xref:System.Windows.Controls.ColumnDefinitionCollection> a <xref:System.Windows.Controls.RowDefinitionCollection> třídy, které provádějí akce, jako je přidání, mazání nebo počítání obsah řádků nebo sloupců. Například můžete <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, nebo <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> položky, které jsou součástí <xref:System.Windows.Controls.ColumnDefinition> nebo <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Windows.Controls.Grid> křížkem <xref:System.Windows.FrameworkElement.Name%2A> z `grid1`. <xref:System.Windows.Controls.Grid> Obsahuje <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Controls.Button> prvky, každý řídí metodu jinou kolekci. Když kliknete <xref:System.Windows.Controls.Button>, aktivuje volání metody v souboru kódu na pozadí.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Tento příklad definuje řadu vlastních metod odpovídající jednotlivým <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru. Můžete změnit počet sloupců a řádků v <xref:System.Windows.Controls.Grid> několika způsoby, které zahrnuje přidání nebo odebrání řádků a sloupců; a monitorovat celkový počet řádků a sloupců. Aby se zabránilo <xref:System.ArgumentOutOfRangeException> a <xref:System.ArgumentException> výjimky, můžete použít funkci kontroly chyb, který <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> metoda poskytuje.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.ColumnDefinitionCollection>
- <xref:System.Windows.Controls.RowDefinitionCollection>
