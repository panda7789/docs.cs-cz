---
title: "Postupy: Překlad elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f9b8363f0c3b9e0a9653dfc9864727c9460f695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="4a13c-102">Postupy: Překlad elementu</span><span class="sxs-lookup"><span data-stu-id="4a13c-102">How to: Translate an Element</span></span>
<span data-ttu-id="4a13c-103">Tento příklad ukazuje, jak převede (přesunout) element pomocí <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="4a13c-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="4a13c-104"><xref:System.Windows.Media.TranslateTransform> Třída je užitečná zejména při přesouvání elementů uvnitř panely, které nepodporují absolutní umístění.</span><span class="sxs-lookup"><span data-stu-id="4a13c-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="4a13c-105">Například při použití <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu, můžete přesunout prvek v rámci <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="4a13c-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="4a13c-106">Použití <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> nastavte velikost, v pixelech, chcete-li přesunout element podél osy x.</span><span class="sxs-lookup"><span data-stu-id="4a13c-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="4a13c-107">Použití <xref:System.Windows.Media.TranslateTransform.Y%2A> vlastnosti a určit velikost, tak v pixelech, chcete-li přesunout element podél osy y.</span><span class="sxs-lookup"><span data-stu-id="4a13c-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="4a13c-108">Nakonec použít <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="4a13c-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="4a13c-109">Následující příklad používá <xref:System.Windows.Media.TranslateTransform> přesunout elementu 50 pixelů do vpravo a 50 pixelů.</span><span class="sxs-lookup"><span data-stu-id="4a13c-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a13c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a13c-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="4a13c-111">Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="4a13c-111">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a13c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a13c-112">See Also</span></span>  
 [<span data-ttu-id="4a13c-113">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="4a13c-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
