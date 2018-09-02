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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404433"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="27ba9-102">Postupy: Přetížení metody panelu OnRender</span><span class="sxs-lookup"><span data-stu-id="27ba9-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="27ba9-103">Tento příklad ukazuje, jak přepsat <xref:System.Windows.Controls.Panel.OnRender%2A> metoda <xref:System.Windows.Controls.Panel> Chcete-li přidat vlastní grafické efekty na prvek rozložení.</span><span class="sxs-lookup"><span data-stu-id="27ba9-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27ba9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="27ba9-104">Example</span></span>  
 <span data-ttu-id="27ba9-105">Použití <xref:System.Windows.Controls.Panel.OnRender%2A> metody, chcete-li přidat grafické efekty na prvek vykreslené panelu.</span><span class="sxs-lookup"><span data-stu-id="27ba9-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="27ba9-106">Například můžete použít tuto metodu Chcete-li přidat vlastní ohraničení nebo účinky na pozadí.</span><span class="sxs-lookup"><span data-stu-id="27ba9-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="27ba9-107">A <xref:System.Windows.Media.DrawingContext> objekt je předán jako argument, který poskytuje metody pro kreslení tvarů, textu, obrázků nebo videa.</span><span class="sxs-lookup"><span data-stu-id="27ba9-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="27ba9-108">V důsledku toho tato metoda je užitečná pro přizpůsobení panelu.</span><span class="sxs-lookup"><span data-stu-id="27ba9-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="27ba9-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="27ba9-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="27ba9-110">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="27ba9-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="27ba9-111">Ukázka vlastních kruhové panelu</span><span class="sxs-lookup"><span data-stu-id="27ba9-111">Custom Radial Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159982)  
 [<span data-ttu-id="27ba9-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="27ba9-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
