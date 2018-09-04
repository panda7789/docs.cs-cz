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
ms.openlocfilehash: 8f3b65bdfe96efdc57c6b8d30991439d3bdb0bc5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506212"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="561bc-102">Postupy: Přetížení metody panelu OnRender</span><span class="sxs-lookup"><span data-stu-id="561bc-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="561bc-103">Tento příklad ukazuje, jak přepsat <xref:System.Windows.Controls.Panel.OnRender%2A> metoda <xref:System.Windows.Controls.Panel> Chcete-li přidat vlastní grafické efekty na prvek rozložení.</span><span class="sxs-lookup"><span data-stu-id="561bc-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="561bc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="561bc-104">Example</span></span>  
 <span data-ttu-id="561bc-105">Použití <xref:System.Windows.Controls.Panel.OnRender%2A> metody, chcete-li přidat grafické efekty na prvek vykreslené panelu.</span><span class="sxs-lookup"><span data-stu-id="561bc-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="561bc-106">Například můžete použít tuto metodu Chcete-li přidat vlastní ohraničení nebo účinky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="561bc-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="561bc-107">A <xref:System.Windows.Media.DrawingContext> objekt je předán jako argument, který poskytuje metody pro kreslení tvarů, textu, obrázků nebo videa.</span><span class="sxs-lookup"><span data-stu-id="561bc-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="561bc-108">V důsledku toho tato metoda je užitečná pro přizpůsobení panelu.</span><span class="sxs-lookup"><span data-stu-id="561bc-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="561bc-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="561bc-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="561bc-110">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="561bc-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="561bc-111">Ukázka vlastních kruhové panelu</span><span class="sxs-lookup"><span data-stu-id="561bc-111">Custom Radial Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159982)  
 [<span data-ttu-id="561bc-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="561bc-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
