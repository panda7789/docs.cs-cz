---
title: 'Postupy: Připojení k vyčíslení'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454437"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="71ccf-102">Postupy: Připojení k vyčíslení</span><span class="sxs-lookup"><span data-stu-id="71ccf-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="71ccf-103">Tento příklad ukazuje, jak vytvořit vazbu na výčet pomocí vazby na metodu GetValues výčtu.</span><span class="sxs-lookup"><span data-stu-id="71ccf-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71ccf-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="71ccf-104">Example</span></span>  
 <span data-ttu-id="71ccf-105">V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazuje seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby.</span><span class="sxs-lookup"><span data-stu-id="71ccf-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="71ccf-106"><xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> jsou vázány tak, že můžete změnit hodnotu vlastnosti <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.Controls.Button> tím, že vyberete hodnotu v <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="71ccf-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="71ccf-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71ccf-107">See also</span></span>

- [<span data-ttu-id="71ccf-108">Vytvoření vazby k metodě</span><span class="sxs-lookup"><span data-stu-id="71ccf-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="71ccf-109">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="71ccf-109">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="71ccf-110">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="71ccf-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
