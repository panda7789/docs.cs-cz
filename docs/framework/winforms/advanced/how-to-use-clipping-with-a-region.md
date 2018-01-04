---
title: "Postupy: Použití oříznutí s oblastí"
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 281ae701bc3e5cee38952a05474360019f76a665
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-clipping-with-a-region"></a>Postupy: Použití oříznutí s oblastí
Jedna z vlastností <xref:System.Drawing.Graphics> třída je klip oblast. Všechny kreslení provádí danou <xref:System.Drawing.Graphics> objekt je omezen na oblasti klip této <xref:System.Drawing.Graphics> objektu. Oblasti klip můžete nastavit tak, že zavoláte <xref:System.Drawing.Graphics.SetClip%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří cestu, která se skládá z jedné mnohoúhelníku. Potom vytvoří kód oblasti, na základě této cesty. Oblast je předána <xref:System.Drawing.Graphics.SetClip%2A> metodu <xref:System.Drawing.Graphics> jsou vykreslovány objekt a potom dva řetězce.  
  
 Následující obrázek znázorňuje oříznutí řetězce.  
  
 ![Klip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Oblasti v rozhraní GDI+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Použití oblastí](../../../../docs/framework/winforms/advanced/using-regions.md)
