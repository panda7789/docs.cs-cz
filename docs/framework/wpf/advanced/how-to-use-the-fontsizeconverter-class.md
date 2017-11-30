---
title: "Postupy: Použití třídy FontSizeConverter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcf2d7348ca5b6b9d3b2edc44f92afbd46d32594
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="e7e84-102">Postupy: Použití třídy FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="e7e84-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="e7e84-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7e84-103">Example</span></span>  
 <span data-ttu-id="e7e84-104">Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.FontSizeConverter> a použít ho chcete-li změnit velikost písma.</span><span class="sxs-lookup"><span data-stu-id="e7e84-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="e7e84-105">V příkladu definuje vlastní metodu s názvem `changeSize` , převede obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Double>a novější do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e7e84-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="e7e84-106">Tato metoda předá <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.FontSizeConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="e7e84-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="e7e84-107">Tato hodnota se potom předá zpět jako hodnota <xref:System.Windows.Controls.TextBlock.FontSize%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="e7e84-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="e7e84-108">Tento příklad také definuje druhý vlastní metodu, která je volána `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="e7e84-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="e7e84-109">Tato metoda převede <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> k <xref:System.String>a pak předá tuto hodnotu <xref:System.Windows.Controls.TextBlock.FontFamily%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="e7e84-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="e7e84-110">Tento příklad nespouští.</span><span class="sxs-lookup"><span data-stu-id="e7e84-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e7e84-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7e84-111">See Also</span></span>  
 <xref:System.Windows.FontSizeConverter>
