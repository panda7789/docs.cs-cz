---
title: 'Postupy: Svázání doplňku pro úpravy s elementem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923498"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="3f4c5-102">Postupy: Svázání doplňku pro úpravy s elementem</span><span class="sxs-lookup"><span data-stu-id="3f4c5-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="3f4c5-103">Tento příklad ukazuje, jak programově navazovat Doplňky na určenou <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3f4c5-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f4c5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f4c5-104">Example</span></span>  
 <span data-ttu-id="3f4c5-105">Chcete-li navazovat Doplňky na konkrétní <xref:System.Windows.UIElement>, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="3f4c5-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="3f4c5-106">`static` Zavolejte metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro získání<xref:System.Windows.Documents.AdornerLayer> objektu ,<xref:System.Windows.UIElement> který má být podrobnější.</span><span class="sxs-lookup"><span data-stu-id="3f4c5-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="3f4c5-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede sestavování vizuálního stromu, počínaje zadaným prvekem **UIElement**a vrátí první nalezenou vrstvu doplňku.</span><span class="sxs-lookup"><span data-stu-id="3f4c5-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="3f4c5-108">(Pokud se nenaleznou žádné vrstvy doplňků, vrátí metoda hodnotu null.)</span><span class="sxs-lookup"><span data-stu-id="3f4c5-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="3f4c5-109">Zavolejte metodu pro svázání doplňku k cílovému prvku **UIElement.** <xref:System.Windows.Documents.AdornerLayer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="3f4c5-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="3f4c5-110">Následující příklad váže SimpleCircleAdorner (zobrazený výše) k <xref:System.Windows.Controls.TextBox> pojmenovanému *MyTextBox*.</span><span class="sxs-lookup"><span data-stu-id="3f4c5-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> <span data-ttu-id="3f4c5-111">Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro svázání doplňku s jiným prvkem není aktuálně podporováno.</span><span class="sxs-lookup"><span data-stu-id="3f4c5-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4c5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f4c5-112">See also</span></span>

- [<span data-ttu-id="3f4c5-113">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="3f4c5-113">Adorners Overview</span></span>](adorners-overview.md)
