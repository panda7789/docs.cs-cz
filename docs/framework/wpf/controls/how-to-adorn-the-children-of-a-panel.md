---
title: 'Postupy: Doplnění podřízených položek panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 4babbf1df57f340a3f6be218f213ad1c868ec9f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550216"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="b3bc1-102">Postupy: Doplnění podřízených položek panelu</span><span class="sxs-lookup"><span data-stu-id="b3bc1-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="b3bc1-103">Tento příklad ukazuje, jak programově vytvořit vazbu adorner podřízené objekty daného zadané <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="b3bc1-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3bc1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3bc1-104">Example</span></span>  
 <span data-ttu-id="b3bc1-105">Při vytváření vazby adorner podřízených objektů daného <xref:System.Windows.Controls.Panel>, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="b3bc1-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b3bc1-106">Deklarovat nové <xref:System.Windows.Documents.AdornerLayer> objekt a volání `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody k vyhledání vrstvu adorner pro element, jehož podřízené objekty mají být ozdobené.</span><span class="sxs-lookup"><span data-stu-id="b3bc1-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="b3bc1-107">Zobrazení výčtu prostřednictvím podřízené objekty daného nadřazeného elementu a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner každý podřízený element.</span><span class="sxs-lookup"><span data-stu-id="b3bc1-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="b3bc1-108">Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) u podřízených objektů daného <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="b3bc1-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="b3bc1-109">Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvořit vazbu adorner jiný element se aktuálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="b3bc1-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bc1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3bc1-110">See Also</span></span>  
 [<span data-ttu-id="b3bc1-111">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="b3bc1-111">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
