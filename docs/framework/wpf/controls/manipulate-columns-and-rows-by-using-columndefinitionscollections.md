---
title: "Postupy: Práce se sloupci a řádky pomocí objektů ColumnDefinitionsCollections a RowDefinitionsCollections"
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
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ba9566e9688984cc881a94e39b065fdadb4cc11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a><span data-ttu-id="f6f5f-102">Postupy: Práce se sloupci a řádky pomocí objektů ColumnDefinitionsCollections a RowDefinitionsCollections</span><span class="sxs-lookup"><span data-stu-id="f6f5f-102">How to: Manipulate Columns and Rows by Using ColumnDefinitionsCollections and RowDefinitionsCollections</span></span>
<span data-ttu-id="f6f5f-103">Tento příklad ukazuje, jak používat metody v <xref:System.Windows.Controls.ColumnDefinitionCollection> a <xref:System.Windows.Controls.RowDefinitionCollection> třídy k provádění akcí, jako je přidání, vymazání nebo počítání obsah řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-103">This example shows how to use the methods in the <xref:System.Windows.Controls.ColumnDefinitionCollection> and <xref:System.Windows.Controls.RowDefinitionCollection> classes to perform actions like adding, clearing, or counting the contents of rows or columns.</span></span> <span data-ttu-id="f6f5f-104">Například můžete <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, nebo <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> položky, které jsou součástí <xref:System.Windows.Controls.ColumnDefinition> nebo <xref:System.Windows.Controls.RowDefinition>.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-104">For example, you can <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, or <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> the items that are included in a <xref:System.Windows.Controls.ColumnDefinition> or <xref:System.Windows.Controls.RowDefinition>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f5f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6f5f-105">Example</span></span>  
 <span data-ttu-id="f6f5f-106">Následující příklad vytvoří <xref:System.Windows.Controls.Grid> element s <xref:System.Windows.FrameworkElement.Name%2A> z `grid1`.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-106">The following example creates a <xref:System.Windows.Controls.Grid> element with a <xref:System.Windows.FrameworkElement.Name%2A> of `grid1`.</span></span> <span data-ttu-id="f6f5f-107"><xref:System.Windows.Controls.Grid> Obsahuje <xref:System.Windows.Controls.StackPanel> , obsahuje <xref:System.Windows.Controls.Button> elementy, každý řídí metoda jinou kolekci.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-107">The <xref:System.Windows.Controls.Grid> contains a <xref:System.Windows.Controls.StackPanel> that holds <xref:System.Windows.Controls.Button> elements, each controlled by a different collection method.</span></span> <span data-ttu-id="f6f5f-108">Když kliknete <xref:System.Windows.Controls.Button>, aktivuje volání metody v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-108">When you click a <xref:System.Windows.Controls.Button>, it activates a method call in the code-behind file.</span></span>  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="f6f5f-109">Tento příklad definuje řadu vlastních metod, každý odpovídající <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-109">This example defines a series of custom methods, each corresponding to a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="f6f5f-110">Můžete změnit počet sloupců a řádků v <xref:System.Windows.Controls.Grid> několika způsoby, což zahrnuje přidání nebo odebrání řádků a sloupců; a poté celkový počet řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-110">You can change the number of columns and rows in the <xref:System.Windows.Controls.Grid> in several ways, which includes adding or removing rows and columns; and counting the total number of rows and columns.</span></span> <span data-ttu-id="f6f5f-111">Aby se zabránilo <xref:System.ArgumentOutOfRangeException> a <xref:System.ArgumentException> výjimky, můžete použít funkci chyb, <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> poskytuje metoda.</span><span class="sxs-lookup"><span data-stu-id="f6f5f-111">To prevent <xref:System.ArgumentOutOfRangeException> and <xref:System.ArgumentException> exceptions, you can use the error-checking functionality that the <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> method provides.</span></span>  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f6f5f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6f5f-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
