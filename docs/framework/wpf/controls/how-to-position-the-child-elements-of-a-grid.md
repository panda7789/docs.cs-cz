---
title: 'Postupy: Umístění podřízených elementů mřížky'
description: Naučte se používat metody Get a set, které jsou definovány v Windows Presentation Foundation mřížce k umístění podřízených elementů.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167394"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="f9012-103">Postupy: Umístění podřízených elementů mřížky</span><span class="sxs-lookup"><span data-stu-id="f9012-103">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="f9012-104">Tento příklad ukazuje, jak použít metody Get a set, které jsou definovány <xref:System.Windows.Controls.Grid> pro k umístění podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="f9012-104">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9012-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9012-105">Example</span></span>  
 <span data-ttu-id="f9012-106">Následující příklad definuje nadřazený <xref:System.Windows.Controls.Grid> element ( `grid1` ), který má tři sloupce a tři řádky.</span><span class="sxs-lookup"><span data-stu-id="f9012-106">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="f9012-107">Podřízený <xref:System.Windows.Shapes.Rectangle> prvek ( `rect1` ) je přidán do <xref:System.Windows.Controls.Grid> pozice sloupce nula, pozice řádku je nula.</span><span class="sxs-lookup"><span data-stu-id="f9012-107">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="f9012-108"><xref:System.Windows.Controls.Button>prvky reprezentují metody, které lze volat pro změnu umístění <xref:System.Windows.Shapes.Rectangle> elementu v rámci <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="f9012-108"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="f9012-109">Když uživatel klikne na tlačítko, je aktivována související metoda.</span><span class="sxs-lookup"><span data-stu-id="f9012-109">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="f9012-110">Následující příklad kódu zpracovává metody, které <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolají události tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f9012-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="f9012-111">Tento příklad zapíše volání těchto metod do <xref:System.Windows.Controls.TextBlock> prvků, které používají související metody get pro výstup nových hodnot vlastností jako řetězců.</span><span class="sxs-lookup"><span data-stu-id="f9012-111">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="f9012-112">Tady je konečný výsledek.</span><span class="sxs-lookup"><span data-stu-id="f9012-112">Here is the finished result!</span></span>

 ![snímek obrazovky znázorňuje uživatelské rozhraní WPF se dvěma sloupci, pravá strana má 3 x 3 mřížky a vlevo obsahuje tlačítka pro přesunutí barevného obdélníku mezi sloupci a řádky mřížky.](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="f9012-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9012-114">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="f9012-115">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="f9012-115">Panels Overview</span></span>](panels-overview.md)
