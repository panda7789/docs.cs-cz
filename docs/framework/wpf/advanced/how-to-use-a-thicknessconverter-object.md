---
title: 'Postupy: Použití objektu ThicknessConverter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: 6c8f9e83468a7b189b96efca2e175c0f3fe0dfff
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735420"
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="68462-102">Postupy: Použití objektu ThicknessConverter</span><span class="sxs-lookup"><span data-stu-id="68462-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="68462-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="68462-103">Example</span></span>  
 <span data-ttu-id="68462-104">Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.ThicknessConverter> a použít ho ke změně tloušťky ohraničení.</span><span class="sxs-lookup"><span data-stu-id="68462-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="68462-105">Příklad definuje vlastní metodu nazvanou `changeThickness`; tato metoda nejprve převede obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Windows.Thickness>a později převede obsah do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="68462-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="68462-106">Tato metoda předává <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.ThicknessConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do instance <xref:System.Windows.Thickness>.</span><span class="sxs-lookup"><span data-stu-id="68462-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="68462-107">Tato hodnota je pak předán zpět jako hodnotu <xref:System.Windows.Controls.Border.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="68462-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="68462-108">V tomto příkladu se nespustí.</span><span class="sxs-lookup"><span data-stu-id="68462-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="68462-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="68462-109">See Also</span></span>  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [<span data-ttu-id="68462-110">Postupy: Změna vlastnosti okraj</span><span class="sxs-lookup"><span data-stu-id="68462-110">How to: Change the Margin Property</span></span>](https://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [<span data-ttu-id="68462-111">Postupy: převod ListBoxItem na nový datový typ.</span><span class="sxs-lookup"><span data-stu-id="68462-111">How to: Convert a ListBoxItem to a new Data Type</span></span>](https://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [<span data-ttu-id="68462-112">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="68462-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
