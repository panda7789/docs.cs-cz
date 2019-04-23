---
title: Použití světové transformace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: f40d7e8cb814344365e8b88c2659751903b79d77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139955"
---
# <a name="using-the-world-transformation"></a>Použití světové transformace
Světové transformace je vlastnost <xref:System.Drawing.Graphics> třídy. Číslo, které určují Světové transformace jsou uložené v <xref:System.Drawing.Drawing2D.Matrix> objektu, který představuje matici 3 x 3. <xref:System.Drawing.Drawing2D.Matrix> a <xref:System.Drawing.Graphics> třídy mají několik metod k nastavení čísla v celém světě transformační matice.  
  
## <a name="different-types-of-transformations"></a>Různé typy transformací  
 V následujícím příkladu kódu nejprve vytvoří obdélník 50 × 50 a vyhledá na počátek (0, 0). Původ v levém horním rohu klientské oblasti.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 Následující kód použije škálování transformaci, která rozšiřuje obdélník faktorem 1,75 ve směru osy x a zmenšuje faktorem 0,5 ve směru osy y obdélníku:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 Výsledkem je obdélník, který je delší ve směru osy x a kratší než původní směru osy y.  
  
 Otočit obdélník místo vertikální snížení jeho kapacity, použijte následující kód:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 Pro převod obdélníku, použijte následující kód:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.Matrix>
- [Systém souřadnic a transformace](coordinate-systems-and-transformations.md)
- [Použití transformací ve spravovaném GDI+](using-transformations-in-managed-gdi.md)
