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
ms.openlocfilehash: a98916555b09e4228908f6b18af765000cdce574
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-custom-layout-engine"></a><span data-ttu-id="0f9b2-102">Postupy: Implementace vlastního modulu pro rozložení</span><span class="sxs-lookup"><span data-stu-id="0f9b2-102">How to: Implement a Custom Layout Engine</span></span>
<span data-ttu-id="0f9b2-103">Následující příklad kódu ukazuje, jak vytvořit vlastní rozložení modul, který provádí jednoduché plovoucí rozložení.</span><span class="sxs-lookup"><span data-stu-id="0f9b2-103">The following code example demonstrates how to create a custom layout engine that performs a simple flow layout.</span></span> <span data-ttu-id="0f9b2-104">Implementuje ovládací prvek panel s názvem `DemoFlowPanel`, která přepisuje <xref:System.Windows.Forms.Control.LayoutEngine%2A> vlastnost, která má poskytovat instance `DemoFlowLayout` třídy.</span><span class="sxs-lookup"><span data-stu-id="0f9b2-104">It implements a panel control named `DemoFlowPanel`, which overrides the <xref:System.Windows.Forms.Control.LayoutEngine%2A> property to provide an instance of the `DemoFlowLayout` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f9b2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f9b2-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0f9b2-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f9b2-106">See Also</span></span>  
 <xref:System.Windows.Forms.Layout.LayoutEngine>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
