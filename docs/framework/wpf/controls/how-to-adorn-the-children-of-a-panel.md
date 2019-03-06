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
ms.openlocfilehash: 9f840180edf55c3e10e6859dfc2b9f4b6495b878
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358188"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="9af21-102">Postupy: Doplnění podřízených položek panelu</span><span class="sxs-lookup"><span data-stu-id="9af21-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="9af21-103">Tento příklad ukazuje, jak prostřednictvím kódu programu připojení doplňku k podřízené položky zadaného <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="9af21-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9af21-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9af21-104">Example</span></span>  
 <span data-ttu-id="9af21-105">K připojení doplňku k podřízených položek <xref:System.Windows.Controls.Panel>, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="9af21-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9af21-106">Deklarovat nový <xref:System.Windows.Documents.AdornerLayer> objektu a volání `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody k vyhledání vrstvu doplněk pro úpravy pro element, jehož potomci mají být opatřený.</span><span class="sxs-lookup"><span data-stu-id="9af21-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="9af21-107">Zobrazit výčet prostřednictvím podřízené objekty nadřazeného elementu a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu připojení doplňku k každý podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="9af21-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="9af21-108">Následující příklad vytvoří vazbu SimpleCircleAdorner (popsaný výš) do podřízených položek <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="9af21-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="9af21-109">Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro vazbu na jiný prvek pro úpravy v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9af21-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af21-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9af21-110">See also</span></span>
- [<span data-ttu-id="9af21-111">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="9af21-111">Adorners Overview</span></span>](adorners-overview.md)
