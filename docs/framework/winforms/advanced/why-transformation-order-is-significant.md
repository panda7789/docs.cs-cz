---
title: Proč je důležité pořadí transformace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 943bfa73b54a1ac5d68d21d2bb6e271133db595a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="why-transformation-order-is-significant"></a>Proč je důležité pořadí transformace
Jediný <xref:System.Drawing.Drawing2D.Matrix> objekt můžete uložit jednu transformaci nebo posloupnost transformace. K tomu se nazývá složený transformace. Matice složené transformace vynásobením matic jednotlivé transformací.  
  
## <a name="composite-transform-examples"></a>Příklady složených transformace  
 V složené transformaci je důležité pořadí jednotlivých transformace. Například pokud nejprve otočit, pak škálování, pak se převede, získáte výsledku jiný než pokud nejprve přeložit, pak otočit pak škálování. V [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], kompozitní transformace jsou integrované zleva doprava. Pokud S R a T škálování, otáčení a překlad matice v uvedeném pořadí, pak produktu SRT aplikace (v tomto pořadí) je matice složené transformace tento první měřítka, pak otočí a pak překládá. Matice vyprodukované produktu SRT aplikace se liší od matice vyprodukované TRS produktu.  
  
 Jedním z důvodů, které pořadí je důležité je, že transformace jako otočení a škálování se provádí s ohledem na původ souřadnicový systém. Škálování objekt, který je umístěn na střed v původu vytvoří jiné výsledky než škálování objekt, který byl přesunut od počátku. Podobně otáčení objekt, který je umístěn na střed v původu vytvoří jiné výsledky než otáčení objekt, který byl přesunut od počátku.  
  
 Následující příklad kombinuje Změna velikosti, otáčení a překlad (v tomto pořadí) k vytvoření složeného transformace. Argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> předaný <xref:System.Drawing.Graphics.RotateTransform%2A> metoda určuje otočení bude sledovat změny velikosti. Podobně, argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> předaný <xref:System.Drawing.Graphics.TranslateTransform%2A> metoda určuje, že překlad bude postupovat podle otočení. <xref:System.Drawing.Drawing2D.MatrixOrder.Append> a <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> jsou členy <xref:System.Drawing.Drawing2D.MatrixOrder> výčtu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 Následující příklad je stejný volání metod jako v předchozím příkladu, ale pořadí volání je obrácený. Výsledné pořadí operací je nejdřív přeložit, pak otočit, a pak otočit škálování, který vytváří velmi jiné výsledky než první škálování, a potom převede.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Jedním ze způsobů pořadí jednotlivých transformace ve složených transformace je pořadí pořadí volání metod. Druhý způsob, jak řídit pořadí operací je změna pořadí argument matice. Následující příklad je stejný jako v předchozím příkladu, vyjma toho, že <xref:System.Drawing.Drawing2D.MatrixOrder.Append> byl změněn na <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. Násobení matic se provádí v pořadí SRT aplikace, kde jsou S R a T matic pro škálování, otáčení a přeložit, v uvedeném pořadí. Pořadí složeného transformace je první škálování, pak otočit a potom převede.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Výsledek okamžitě předchozí příklad je stejný jako výsledek v prvním příkladu v tomto tématu. Je to proto, že jsme obrácený pořadí volání metod a pořadí násobení matic.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Použití transformací ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
