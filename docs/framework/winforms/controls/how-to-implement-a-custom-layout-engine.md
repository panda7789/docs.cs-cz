---
title: "Postupy: Implementace vlastního modulu pro rozložení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- layout engines [Windows Forms], custom
- TableLayoutPanel control [Windows Forms], layout engine
- layout engines [Windows Forms], implementing
- FlowLayoutPanel control [Windows Forms], layout engine
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fa46aaf2546200095589deffe95e9ccf2991021
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-custom-layout-engine"></a><span data-ttu-id="c70f4-102">Postupy: Implementace vlastního modulu pro rozložení</span><span class="sxs-lookup"><span data-stu-id="c70f4-102">How to: Implement a Custom Layout Engine</span></span>
<span data-ttu-id="c70f4-103">Následující příklad kódu ukazuje, jak vytvořit vlastní rozložení modul, který provádí jednoduché plovoucí rozložení.</span><span class="sxs-lookup"><span data-stu-id="c70f4-103">The following code example demonstrates how to create a custom layout engine that performs a simple flow layout.</span></span> <span data-ttu-id="c70f4-104">Implementuje ovládací prvek panel s názvem `DemoFlowPanel`, která přepisuje <xref:System.Windows.Forms.Control.LayoutEngine%2A> vlastnost, která má poskytovat instance `DemoFlowLayout` třídy.</span><span class="sxs-lookup"><span data-stu-id="c70f4-104">It implements a panel control named `DemoFlowPanel`, which overrides the <xref:System.Windows.Forms.Control.LayoutEngine%2A> property to provide an instance of the `DemoFlowLayout` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c70f4-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70f4-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c70f4-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="c70f4-106">See Also</span></span>  
 <xref:System.Windows.Forms.Layout.LayoutEngine>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
