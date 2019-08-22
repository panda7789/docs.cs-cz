---
title: 'Postupy: Přepsání metody panelu OnRender'
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
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666706"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="8d3f7-102">Postupy: Přepsání metody panelu OnRender</span><span class="sxs-lookup"><span data-stu-id="8d3f7-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="8d3f7-103">Tento příklad ukazuje, jak přepsat <xref:System.Windows.Controls.Panel.OnRender%2A> <xref:System.Windows.Controls.Panel> metodu pro přidání vlastních grafických efektů do prvku rozložení.</span><span class="sxs-lookup"><span data-stu-id="8d3f7-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d3f7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d3f7-104">Example</span></span>  
 <span data-ttu-id="8d3f7-105"><xref:System.Windows.Controls.Panel.OnRender%2A> Použijte metodu pro přidání grafických efektů do vykresleného panelu elementu.</span><span class="sxs-lookup"><span data-stu-id="8d3f7-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="8d3f7-106">Můžete například použít tuto metodu k přidání vlastních efektů ohraničení nebo pozadí.</span><span class="sxs-lookup"><span data-stu-id="8d3f7-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="8d3f7-107"><xref:System.Windows.Media.DrawingContext> Objekt je předán jako argument, který poskytuje metody pro kreslení tvarů, textu, obrázků a videí.</span><span class="sxs-lookup"><span data-stu-id="8d3f7-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="8d3f7-108">V důsledku toho je tato metoda užitečná pro přizpůsobení objektu panelu.</span><span class="sxs-lookup"><span data-stu-id="8d3f7-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8d3f7-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d3f7-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="8d3f7-110">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="8d3f7-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="8d3f7-111">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8d3f7-111">How-to Topics</span></span>](panel-how-to-topics.md)
