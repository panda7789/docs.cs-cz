---
title: 'Postupy: Vytvoření vlastního elementu panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 2d1581ef1d0130a6952becf36d668e6a198e1ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552397"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="116a3-102">Postupy: Vytvoření vlastního elementu panelu</span><span class="sxs-lookup"><span data-stu-id="116a3-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="116a3-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="116a3-103">Example</span></span>  
 <span data-ttu-id="116a3-104">Tento příklad ukazuje, jak lze přepsat výchozí chování rozložení <xref:System.Windows.Controls.Panel> elementu a vytvořit vlastní rozložení elementy, které jsou odvozeny od <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="116a3-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="116a3-105">V příkladu definuje jednoduché vlastní <xref:System.Windows.Controls.Panel> prvek s názvem `PlotPanel`, který umisťuje podřízených elementů podle dvě pevně souřadnic x a y-.</span><span class="sxs-lookup"><span data-stu-id="116a3-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="116a3-106">V tomto příkladu `x` a `y` jsou nastaveny na `50`; proto jsou všechny podřízené prvky umístěny v tomto umístění na x a y osy.</span><span class="sxs-lookup"><span data-stu-id="116a3-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="116a3-107">K implementaci vlastních <xref:System.Windows.Controls.Panel> chování, v příkladu se používá <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="116a3-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="116a3-108">Každá metoda vrátí <xref:System.Windows.Size> data, která je nutné umístit a vykreslit podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="116a3-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="116a3-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="116a3-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="116a3-110">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="116a3-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="116a3-111">Vytvořit vlastní vzorek panely obsah zabalení</span><span class="sxs-lookup"><span data-stu-id="116a3-111">Create a Custom Content-Wrapping Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159979)
