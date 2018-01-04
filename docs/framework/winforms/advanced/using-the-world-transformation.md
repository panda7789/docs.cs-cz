---
title: "Použití světové transformace"
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
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8599f2e154e05fd2d43b094041989c4a3a5dbc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-world-transformation"></a>Použití světové transformace
Světové transformace je vlastnost <xref:System.Drawing.Graphics> třídy. Čísla, které určují Světové transformace jsou uložené v <xref:System.Drawing.Drawing2D.Matrix> objekt, který představuje matici 3 x 3. <xref:System.Drawing.Drawing2D.Matrix> a <xref:System.Drawing.Graphics> třídy mají několik metod pro nastavení čísla v transformační matice world.  
  
## <a name="different-types-of-transformations"></a>Různé typy transformací  
 V následujícím příkladu kódu nejprve vytvoří obdélník 50 × 50 a vyhledá v původu (0, 0). Pochází v levém horním rohu klientské oblasti.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 Následující kód použije škálování transformaci, která rozšiřuje rámeček faktorem 1,75 ve směru osy x a zmenší rámeček faktorem 0,5 ve směru osy y:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 Výsledkem je obdélníku, který je delší ve směru osy x a ve směru osy y kratší než původní.  
  
 Otočit rámeček místo škálování ji, použijte následující kód:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 Chcete-li přeložit rámeček, použijte následující kód:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Použití transformací ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
