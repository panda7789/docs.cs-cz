---
title: 'Postupy: Přetížení metody panelu OnRender'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: e591bc195d3b0ba58002bda42ddb3e9ed35d312e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554869"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="a9247-102">Postupy: Přetížení metody panelu OnRender</span><span class="sxs-lookup"><span data-stu-id="a9247-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="a9247-103">Tento příklad ukazuje, jak lze přepsat <xref:System.Windows.Controls.Panel.OnRender%2A> metodu <xref:System.Windows.Controls.Panel> Chcete-li přidat vlastní grafické efekty do elementu rozložení.</span><span class="sxs-lookup"><span data-stu-id="a9247-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9247-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9247-104">Example</span></span>  
 <span data-ttu-id="a9247-105">Použití <xref:System.Windows.Controls.Panel.OnRender%2A> metoda-li přidat grafické efekty vykreslené panel prvek.</span><span class="sxs-lookup"><span data-stu-id="a9247-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="a9247-106">Například můžete použít tuto metodu můžete přidat vlastní ohraničení nebo pozadí účinky.</span><span class="sxs-lookup"><span data-stu-id="a9247-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="a9247-107">A <xref:System.Windows.Media.DrawingContext> objektu je předat jako argument, který poskytuje metody pro kreslení tvarů, text, obrázky nebo videa.</span><span class="sxs-lookup"><span data-stu-id="a9247-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="a9247-108">V důsledku toho tato metoda je užitečná pro přizpůsobení panelů objektu.</span><span class="sxs-lookup"><span data-stu-id="a9247-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a9247-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9247-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="a9247-110">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="a9247-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="a9247-111">Vlastní paprskového panelu ukázkové</span><span class="sxs-lookup"><span data-stu-id="a9247-111">Custom Radial Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [<span data-ttu-id="a9247-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a9247-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
