---
title: "Postupy: Vytvoření a použití objektu GridLengthConverter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 300916ec102682e1d886d43fbe70eeaf088d6454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="9d568-102">Postupy: Vytvoření a použití objektu GridLengthConverter</span><span class="sxs-lookup"><span data-stu-id="9d568-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="9d568-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d568-103">Example</span></span>  
 <span data-ttu-id="9d568-104">Následující příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.GridLengthConverter>.</span><span class="sxs-lookup"><span data-stu-id="9d568-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="9d568-105">V příkladu definuje vlastní metodu s názvem `changeCol`, který předává <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.GridLengthConverter> , která převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Windows.GridLength>.</span><span class="sxs-lookup"><span data-stu-id="9d568-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="9d568-106">Převedená hodnota se potom předá zpět jako hodnota <xref:System.Windows.Controls.ColumnDefinition.Width%2A> vlastnost <xref:System.Windows.Controls.ColumnDefinition> elementu.</span><span class="sxs-lookup"><span data-stu-id="9d568-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="9d568-107">V příkladu definuje také druhý vlastní metodu, s názvem `changeColVal`.</span><span class="sxs-lookup"><span data-stu-id="9d568-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="9d568-108">Tato vlastní metoda převede <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> z <xref:System.Windows.Controls.Slider> k <xref:System.String> a potom předává, které hodnoty zpět do <xref:System.Windows.Controls.ColumnDefinition> jako <xref:System.Windows.Controls.ColumnDefinition.Width%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="9d568-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="9d568-109">Všimněte si, že samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor definuje obsah <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="9d568-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9d568-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d568-110">See Also</span></span>  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
