---
title: "Postupy: Připojení doplňku k elementu"
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
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3c657cde9da19f8ebc6b6d4d05077ed027781b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="5fc4e-102">Postupy: Připojení doplňku k elementu</span><span class="sxs-lookup"><span data-stu-id="5fc4e-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="5fc4e-103">Tento příklad ukazuje, jak se prostřednictvím kódu programu vytvořit vazbu adorner do určeného <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="5fc4e-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fc4e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fc4e-104">Example</span></span>  
 <span data-ttu-id="5fc4e-105">K vytvoření vazby adorner konkrétní <xref:System.Windows.UIElement>, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="5fc4e-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5fc4e-106">Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> získat <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> k být ozdobené.</span><span class="sxs-lookup"><span data-stu-id="5fc4e-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="5fc4e-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede až vizuálním stromu, začínající v zadaném **prvků uživatelského rozhraní**a vrátí první vrstvu adorner najde.</span><span class="sxs-lookup"><span data-stu-id="5fc4e-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="5fc4e-108">(Pokud se nenajdou žádné adorner vrstvy, metoda vrátí hodnotu null.)</span><span class="sxs-lookup"><span data-stu-id="5fc4e-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="5fc4e-109">Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner k cíli **prvků uživatelského rozhraní**.</span><span class="sxs-lookup"><span data-stu-id="5fc4e-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="5fc4e-110">Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="5fc4e-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="5fc4e-111">Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvořit vazbu adorner jiný element se aktuálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="5fc4e-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc4e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fc4e-112">See Also</span></span>  
 [<span data-ttu-id="5fc4e-113">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="5fc4e-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
