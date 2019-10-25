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
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799143"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="ada1b-102">Postupy: Vytvoření vlastního elementu panelu</span><span class="sxs-lookup"><span data-stu-id="ada1b-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="ada1b-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="ada1b-103">Example</span></span>  
 <span data-ttu-id="ada1b-104">Tento příklad ukazuje, jak přepsat výchozí chování rozložení prvku <xref:System.Windows.Controls.Panel> a vytvořit vlastní prvky rozložení, které jsou odvozeny z <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="ada1b-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="ada1b-105">Příklad definuje jednoduchý prvek vlastní <xref:System.Windows.Controls.Panel> s názvem `PlotPanel`, který umístí podřízené prvky podle dvou pevně zakódovaných souřadnic x-a y.</span><span class="sxs-lookup"><span data-stu-id="ada1b-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="ada1b-106">V tomto příkladu jsou `x` a `y` obě nastaveny na `50`; Proto jsou všechny podřízené prvky umístěny v tomto umístění na osách x a y.</span><span class="sxs-lookup"><span data-stu-id="ada1b-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="ada1b-107">K implementaci vlastního chování <xref:System.Windows.Controls.Panel> používá tento příklad metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.</span><span class="sxs-lookup"><span data-stu-id="ada1b-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="ada1b-108">Každá metoda vrátí <xref:System.Windows.Size> data, která jsou nutná k umístění a vykreslení podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="ada1b-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ada1b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ada1b-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="ada1b-110">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="ada1b-110">Panels Overview</span></span>](panels-overview.md)
