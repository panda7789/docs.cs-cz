---
title: "Postupy: Použití testování průchodu s oblastí"
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
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c0766c989df7c2329aa4d36af834378b02b1301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Postupy: Použití testování průchodu s oblastí
Účelem testování přístupů je určit, zda je kurzor přes daný objekt, jako je například ikony nebo tlačítko.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří oblast ve tvaru plus tvořících sjednocení dvou obdélníkovou oblastí. Předpokládáme, že proměnná `point` obsahuje umístění a klikněte na poslední. Kód zkontroluje, zda `point` v oblasti ve tvaru plus. Pokud je bod je v oblasti (stiskněte klávesu), je oblast vyplněn neprůhledného red štětce. Oblast, jinak je vyplněn poloprůhledných red štětce.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Region>  
 [Oblasti v rozhraní GDI+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Postupy: Použití oříznutí s oblastí](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
