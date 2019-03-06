---
title: 'Postupy: Připojení doplňku k elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: 4943121aaf8ee6524be3fc9004eafee4fa92e527
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353917"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="3c572-102">Postupy: Připojení doplňku k elementu</span><span class="sxs-lookup"><span data-stu-id="3c572-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="3c572-103">Tento příklad ukazuje, jak prostřednictvím kódu programu připojení doplňku k zadané <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3c572-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c572-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c572-104">Example</span></span>  
 <span data-ttu-id="3c572-105">K připojení doplňku k konkrétní <xref:System.Windows.UIElement>, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="3c572-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3c572-106">Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> získat <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> chcete být opatřený.</span><span class="sxs-lookup"><span data-stu-id="3c572-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="3c572-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> provede se vizuální strom začínající v zadaném **UIElement**a vrátí první vrstvu doplněk pro úpravy, které nalezne.</span><span class="sxs-lookup"><span data-stu-id="3c572-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="3c572-108">(Pokud se nenajdou žádné vrstvy doplněk pro úpravy, metoda vrátí hodnotu null.)</span><span class="sxs-lookup"><span data-stu-id="3c572-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="3c572-109">Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro vytvoření vazby doplněk pro úpravy k cíli **UIElement**.</span><span class="sxs-lookup"><span data-stu-id="3c572-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="3c572-110">Následující příklad vytvoří vazbu SimpleCircleAdorner (popsaný výš) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="3c572-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="3c572-111">Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro vazbu na jiný prvek pro úpravy v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="3c572-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c572-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c572-112">See also</span></span>
- [<span data-ttu-id="3c572-113">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="3c572-113">Adorners Overview</span></span>](adorners-overview.md)
