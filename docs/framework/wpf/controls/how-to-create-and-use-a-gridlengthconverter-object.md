---
title: 'Postupy: Vytvoření a použití objektu GridLengthConverter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: 0455d91eff820e5c087af20207ece1313f6f3a39
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352253"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="8d074-102">Postupy: Vytvoření a použití objektu GridLengthConverter</span><span class="sxs-lookup"><span data-stu-id="8d074-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="8d074-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d074-103">Example</span></span>  
 <span data-ttu-id="8d074-104">Následující příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.GridLengthConverter>.</span><span class="sxs-lookup"><span data-stu-id="8d074-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="8d074-105">Příklad definuje vlastní metodu s názvem `changeCol`, která předá <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.GridLengthConverter> , která převede <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do instance <xref:System.Windows.GridLength>.</span><span class="sxs-lookup"><span data-stu-id="8d074-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="8d074-106">Převedená hodnota je pak předán zpět jako hodnotu <xref:System.Windows.Controls.ColumnDefinition.Width%2A> vlastnost <xref:System.Windows.Controls.ColumnDefinition> elementu.</span><span class="sxs-lookup"><span data-stu-id="8d074-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="8d074-107">Příklad také definuje druhá vlastní metoda volána `changeColVal`.</span><span class="sxs-lookup"><span data-stu-id="8d074-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="8d074-108">Tato vlastní metoda převede <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> z <xref:System.Windows.Controls.Slider> k <xref:System.String> a pak předá, které hodnotu zpět na <xref:System.Windows.Controls.ColumnDefinition> jako <xref:System.Windows.Controls.ColumnDefinition.Width%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="8d074-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="8d074-109">Všimněte si, že samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor definuje obsah <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="8d074-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8d074-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d074-110">See also</span></span>
- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
