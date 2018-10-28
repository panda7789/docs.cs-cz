---
title: 'Postupy: Umístění podřízených elementů mřížky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 5ccdcb3d166e1b703faff1dc8046e61ee213d12a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186987"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="84e02-102">Postupy: Umístění podřízených elementů mřížky</span><span class="sxs-lookup"><span data-stu-id="84e02-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="84e02-103">Tento příklad ukazuje způsob použití get a set metod, které jsou definovány na <xref:System.Windows.Controls.Grid> umístění podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="84e02-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84e02-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="84e02-104">Example</span></span>  
 <span data-ttu-id="84e02-105">Následující příklad definuje nadřazený <xref:System.Windows.Controls.Grid> – element (`grid1`), který má tři sloupce a tři řádky.</span><span class="sxs-lookup"><span data-stu-id="84e02-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="84e02-106">Podřízený <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) se přidá do <xref:System.Windows.Controls.Grid> v pozici sloupce nula, řádek pozici nula.</span><span class="sxs-lookup"><span data-stu-id="84e02-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="84e02-107"><xref:System.Windows.Controls.Button> elementy reprezentují metody, které lze volat pro přemístění <xref:System.Windows.Shapes.Rectangle> element v rámci <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="84e02-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="84e02-108">Když uživatel klikne na tlačítko, je aktivováno související metody.</span><span class="sxs-lookup"><span data-stu-id="84e02-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="84e02-109">Následující příklad použití modelu code-behind zpracovává metody, která tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="84e02-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="84e02-110">Tento příklad zapíše tato volání metody <xref:System.Windows.Controls.TextBlock> prvky, které týkající se použití metody get na výstup nové hodnoty vlastnosti jako řetězce.</span><span class="sxs-lookup"><span data-stu-id="84e02-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="84e02-111">Tady je výsledku dokončeno!</span><span class="sxs-lookup"><span data-stu-id="84e02-111">Here is the finished result!</span></span>
 
 ![snímek obrazovky znázorňuje uživatelské rozhraní WPF se dvěma sloupci, pravé straně má mřížka 3 × 3 a levé straně tlačítka Přesunout barevný obdélník mezi sloupci a řádky mřížky](./media/grid-methods-sample.png) 
  
## <a name="see-also"></a><span data-ttu-id="84e02-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="84e02-113">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="84e02-114">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="84e02-114">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
