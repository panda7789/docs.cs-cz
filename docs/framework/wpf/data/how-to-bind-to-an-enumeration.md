---
title: 'Postupy: Připojení k vyčíslení'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: df26d2bd08e4691837f739a4e71d3bb1a25bdd00
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377791"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="c2b0e-102">Postupy: Připojení k vyčíslení</span><span class="sxs-lookup"><span data-stu-id="c2b0e-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="c2b0e-103">Tento příklad ukazuje, jak připojení k vyčíslení navázáním metoda GetValues výčtu.</span><span class="sxs-lookup"><span data-stu-id="c2b0e-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2b0e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2b0e-104">Example</span></span>  
 <span data-ttu-id="c2b0e-105">V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazí seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby.</span><span class="sxs-lookup"><span data-stu-id="c2b0e-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="c2b0e-106"><xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> vázány tak, že můžete změnit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotu vlastnosti <xref:System.Windows.Controls.Button> tak, že vyberete hodnotu v <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="c2b0e-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="c2b0e-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2b0e-107">See also</span></span>
- [<span data-ttu-id="c2b0e-108">Vytvoření vazby k metodě</span><span class="sxs-lookup"><span data-stu-id="c2b0e-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="c2b0e-109">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="c2b0e-109">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="c2b0e-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c2b0e-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
