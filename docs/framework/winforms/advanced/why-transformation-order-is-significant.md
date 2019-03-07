---
title: Proč je důležité pořadí transformace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order significance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 9fd0764e3e3754fbbaa16441737e0463db3f99a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503174"
---
# <a name="why-transformation-order-is-significant"></a>Proč je důležité pořadí transformace

Jediný <xref:System.Drawing.Drawing2D.Matrix> objekt uložit jednu transformaci nebo posloupnost transformace. Druhá možnost se nazývá kompozitní transformace. Matice kompozitní transformace vynásobením matice jednotlivé transformace.

## <a name="composite-transform-examples"></a>Příklady kompozitní transformace

V kompozitní transformace je důležité pořadí jednotlivých transformace. Například pokud nejprve otočit, pak škálovat, pak se překlad, můžete získat jiné výsledky než pokud nejprve přeložit, pak otočit a potom vertikálně. V [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], kompozitní transformace jsou vytvořeny zleva doprava. Pokud S R jsou a T škálování, otočení a překladu matic v uvedeném pořadí, pak produktu SRT aplikace (v uvedeném pořadí) matice kompozitní transformace, která se škáluje první, potom otočí, pak se přeloží. Matice vytvářených produktu SRT aplikace se liší od matice vytvářených TRS produktu.

Jeden z důvodů, proč je důležité pořadí je, že transformací například rotace a změnu měřítka hotovi s ohledem na počátku systém souřadnic. Škálování, které jsou zaměřeny na počátek objekt vytvoří jiné výsledky než škálování objekt, který byl přesunut mimo původu. Podobně otáčení objektu, které jsou zaměřeny na počátek vytvoří jiné výsledky než otáčení objektu, který byl přesunut mimo původu.

Následující příklad kombinuje škálování, otočení a překladu (v uvedeném pořadí) k vytvoření kompozitní transformace. Argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> předán <xref:System.Drawing.Graphics.RotateTransform%2A> metoda označuje, že bude následovat otočení škálování. Podobně, argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> předán <xref:System.Drawing.Graphics.TranslateTransform%2A> metoda označuje, že překlad bude následovat otočení. <xref:System.Drawing.Drawing2D.MatrixOrder.Append> a <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> jsou členy <xref:System.Drawing.Drawing2D.MatrixOrder> výčtu.

[!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
[!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]

Následující příklad provede volání stejné metody jako v předchozím příkladu, ale je obrácený pořadí volání. Výsledné pořadí operací je nejprve přeložit, pak otočit, a potom otočit škálování, který vytváří velmi jiné výsledky než první škálování, a pak přeložit.

[!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
[!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]

Jedním ze způsobů pořadí jednotlivých transformace v kompozitní transformace je obrácené pořadí posloupnost volání metody. Druhý způsob, jak řídit pořadí operací je změna pořadí argument matice. Následující příklad je stejný jako předchozí příklad s výjimkou, že <xref:System.Drawing.Drawing2D.MatrixOrder.Append> byl změněn na <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. Násobení matic se provádí v pořadí SRT aplikace, kde je S, R a T matice pro škálování, otáčení a přeložit, v uvedeném pořadí. Pořadí kompozitní transformace je první škálovací otočit pak přeložit.

[!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
[!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]

Výsledek bezprostředně předcházející příklad je stejný jako výsledek první příklad v tomto tématu. Je to proto, že jsme obrácený pořadí volání metod a pořadí násobení matic.

## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.Matrix>
- [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
- [Použití transformací ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
