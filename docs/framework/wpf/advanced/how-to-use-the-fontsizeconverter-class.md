---
title: 'Postupy: Použití třídy FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545123"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="0aac4-102">Postupy: Použití třídy FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="0aac4-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="0aac4-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="0aac4-103">Example</span></span>  
 <span data-ttu-id="0aac4-104">Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.FontSizeConverter> a použít ho chcete-li změnit velikost písma.</span><span class="sxs-lookup"><span data-stu-id="0aac4-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="0aac4-105">V příkladu definuje vlastní metodu s názvem `changeSize` , převede obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Double>a novější do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0aac4-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="0aac4-106">Tato metoda předá <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.FontSizeConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="0aac4-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="0aac4-107">Tato hodnota se potom předá zpět jako hodnota <xref:System.Windows.Controls.TextBlock.FontSize%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="0aac4-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="0aac4-108">Tento příklad také definuje druhý vlastní metodu, která je volána `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="0aac4-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="0aac4-109">Tato metoda převede <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> k <xref:System.String>a pak předá tuto hodnotu <xref:System.Windows.Controls.TextBlock.FontFamily%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="0aac4-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="0aac4-110">Tento příklad nespouští.</span><span class="sxs-lookup"><span data-stu-id="0aac4-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0aac4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0aac4-111">See Also</span></span>  
 <xref:System.Windows.FontSizeConverter>
