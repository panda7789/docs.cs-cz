---
title: 'Postupy: Použití třídy FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 21050ae69ad834b56c70f40d85138714af334dab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364096"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="27c35-102">Postupy: Použití třídy FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="27c35-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="27c35-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="27c35-103">Example</span></span>  
 <span data-ttu-id="27c35-104">Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.FontSizeConverter> a použít ho ke změně velikosti písma.</span><span class="sxs-lookup"><span data-stu-id="27c35-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="27c35-105">Příklad definuje vlastní metodu nazvanou `changeSize` , která převede obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Double>nebo novější do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="27c35-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="27c35-106">Tato metoda předává <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.FontSizeConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do instance <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="27c35-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="27c35-107">Tato hodnota je pak předán zpět jako hodnotu <xref:System.Windows.Controls.TextBlock.FontSize%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="27c35-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="27c35-108">Tento příklad také definuje druhý vlastní metodu, která je volána `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="27c35-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="27c35-109">Tato metoda převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> k <xref:System.String>a poté předá tuto hodnotu <xref:System.Windows.Controls.TextBlock.FontFamily%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="27c35-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="27c35-110">V tomto příkladu se nespustí.</span><span class="sxs-lookup"><span data-stu-id="27c35-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="27c35-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27c35-111">See also</span></span>
- <xref:System.Windows.FontSizeConverter>
