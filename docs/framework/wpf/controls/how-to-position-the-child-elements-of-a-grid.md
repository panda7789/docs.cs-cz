---
title: 'Postupy: Umístění podřízených elementů mřížky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186724"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="a688a-102">Postupy: Umístění podřízených elementů mřížky</span><span class="sxs-lookup"><span data-stu-id="a688a-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="a688a-103">Tento příklad ukazuje, jak používat get a <xref:System.Windows.Controls.Grid> set metody, které jsou definovány na umístění podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="a688a-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a688a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a688a-104">Example</span></span>  
 <span data-ttu-id="a688a-105">Následující příklad definuje nadřazený <xref:System.Windows.Controls.Grid> prvek (`grid1`), který má tři sloupce a tři řádky.</span><span class="sxs-lookup"><span data-stu-id="a688a-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="a688a-106">Podřízený <xref:System.Windows.Shapes.Rectangle> prvek`rect1`( ) <xref:System.Windows.Controls.Grid> je přidán do pozice ve sloupci nula, pozice řádku nula.</span><span class="sxs-lookup"><span data-stu-id="a688a-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="a688a-107"><xref:System.Windows.Controls.Button>prvky představují metody, které lze <xref:System.Windows.Shapes.Rectangle> volat <xref:System.Windows.Controls.Grid>ke přemístění prvku v rámci .</span><span class="sxs-lookup"><span data-stu-id="a688a-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="a688a-108">Když uživatel klepne na tlačítko, aktivuje se související metoda.</span><span class="sxs-lookup"><span data-stu-id="a688a-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="a688a-109">Následující příklad na pozadí kódu zpracovává metody, které vyvolat události tlačítka. <xref:System.Windows.Controls.Primitives.ButtonBase.Click></span><span class="sxs-lookup"><span data-stu-id="a688a-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="a688a-110">Příklad zapisuje <xref:System.Windows.Controls.TextBlock> tyto metody volání prvků, které používají související get metody k výstupu nové hodnoty vlastností jako řetězce.</span><span class="sxs-lookup"><span data-stu-id="a688a-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="a688a-111">Zde je hotový výsledek!</span><span class="sxs-lookup"><span data-stu-id="a688a-111">Here is the finished result!</span></span>

 ![snímek obrazovky znázorňuje uživatelské rozhraní WPF se dvěma sloupci, pravá strana má mřížku 3 x 3 a vlevo má tlačítka pro pohyb barevného obdélníku mezi sloupci a řádky mřížky](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="a688a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a688a-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="a688a-114">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="a688a-114">Panels Overview</span></span>](panels-overview.md)
