---
title: 'Postupy: Vytvoření vazby k výčtu'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 5026261366d6abde82790f05780d8ba2c29c4a49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210019"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="281df-102">Postupy: Vytvoření vazby k výčtu</span><span class="sxs-lookup"><span data-stu-id="281df-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="281df-103">Tento příklad ukazuje, jak připojení k vyčíslení navázáním metoda GetValues výčtu.</span><span class="sxs-lookup"><span data-stu-id="281df-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="281df-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="281df-104">Example</span></span>  
 <span data-ttu-id="281df-105">V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazí seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby.</span><span class="sxs-lookup"><span data-stu-id="281df-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="281df-106"><xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> vázány tak, že můžete změnit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotu vlastnosti <xref:System.Windows.Controls.Button> tak, že vyberete hodnotu v <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="281df-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="281df-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="281df-107">See also</span></span>

- [<span data-ttu-id="281df-108">Vytvoření vazby k metodě</span><span class="sxs-lookup"><span data-stu-id="281df-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="281df-109">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="281df-109">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="281df-110">– postupy</span><span class="sxs-lookup"><span data-stu-id="281df-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
