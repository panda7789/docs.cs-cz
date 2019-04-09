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
ms.openlocfilehash: d4fc9d76ada9f27bd52619280b323691af9382c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139565"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="dad12-102">Postupy: Vytvoření vlastního elementu panelu</span><span class="sxs-lookup"><span data-stu-id="dad12-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="dad12-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="dad12-103">Example</span></span>  
 <span data-ttu-id="dad12-104">Tento příklad ukazuje, jak přepsat výchozí chování rozložení <xref:System.Windows.Controls.Panel> elementu a vytvářet vlastní rozložení prvků, které jsou odvozeny z <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="dad12-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="dad12-105">V příkladu je definována jednoduchý vlastní <xref:System.Windows.Controls.Panel> prvek s názvem `PlotPanel`, které se umístí podřízené prvky podle dvě pevně zakódované souřadnic x a y-.</span><span class="sxs-lookup"><span data-stu-id="dad12-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="dad12-106">V tomto příkladu `x` a `y` jsou nastaveny na `50`; proto všechny podřízené prvky jsou umístěny na tomto místě na x a y osy.</span><span class="sxs-lookup"><span data-stu-id="dad12-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="dad12-107">K implementaci vlastní <xref:System.Windows.Controls.Panel> chování, v příkladu se používá <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dad12-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="dad12-108">Každá metoda vrátí <xref:System.Windows.Size> data, která je potřeba umístit a vykreslování podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="dad12-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dad12-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dad12-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="dad12-110">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="dad12-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="dad12-111">Vytvoření vlastního panelu ukázky zabalení obsahu</span><span class="sxs-lookup"><span data-stu-id="dad12-111">Create a Custom Content-Wrapping Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159979)
