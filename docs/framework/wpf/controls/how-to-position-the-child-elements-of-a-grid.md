---
title: "Postupy: Umístění podřízených elementů mřížky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ca385e1aee10fb10ac3e912999aec3a11d03ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="1a0f2-102">Postupy: Umístění podřízených elementů mřížky</span><span class="sxs-lookup"><span data-stu-id="1a0f2-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="1a0f2-103">Tento příklad ukazuje, jak používat get a nastavit metody, které jsou definovány na <xref:System.Windows.Controls.Grid> na pozici podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="1a0f2-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a0f2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a0f2-104">Example</span></span>  
 <span data-ttu-id="1a0f2-105">V následujícím příkladu definuje nadřazený <xref:System.Windows.Controls.Grid> – element (`grid1`), má tři sloupce a tři řádky.</span><span class="sxs-lookup"><span data-stu-id="1a0f2-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="1a0f2-106">Podřízenou <xref:System.Windows.Shapes.Rectangle> element (`rect1`) je přidán do <xref:System.Windows.Controls.Grid> v pozici sloupce nula, řádek pozice nula.</span><span class="sxs-lookup"><span data-stu-id="1a0f2-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="1a0f2-107"><xref:System.Windows.Controls.Button>elementy reprezentují metody, které lze volat pro změnu umístění <xref:System.Windows.Shapes.Rectangle> v rámci <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="1a0f2-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="1a0f2-108">Když uživatel klikne na tlačítko, je aktivována související metody.</span><span class="sxs-lookup"><span data-stu-id="1a0f2-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="1a0f2-109">Následující příklad kódu zpracovává metody, tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="1a0f2-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="1a0f2-110">V příkladu je zapsán těchto volání metody <xref:System.Windows.Controls.TextBlock> prvky, které používá související získat metody pro výstup nové hodnoty vlastností jako řetězce.</span><span class="sxs-lookup"><span data-stu-id="1a0f2-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1a0f2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a0f2-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="1a0f2-112">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="1a0f2-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
