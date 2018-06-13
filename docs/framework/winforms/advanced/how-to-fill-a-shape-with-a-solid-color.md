---
title: 'Postupy: Vyplnění obrazce plnou barvou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: 7f719417a6a1226d7dc4d600518711ba31920a6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521320"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Postupy: Vyplnění obrazce plnou barvou
Vyplnění obrazce plnou barvou, vytvořte <xref:System.Drawing.SolidBrush> objektu a poté předat, <xref:System.Drawing.SolidBrush> objektu jako argument pro jednu z metod výplně <xref:System.Drawing.Graphics> třídy. Následující příklad ukazuje, jak k vyplnění elipsy s červenou barvu.  
  
## <a name="example"></a>Příklad  
 V následujícím kódu <xref:System.Drawing.SolidBrush.%23ctor%2A> konstruktor přijímá <xref:System.Drawing.Color> objektu jako jeho jediným argumentem. Hodnoty používané <xref:System.Drawing.Color.FromArgb%2A> metoda představují součásti alfa, červené, zelené a modré barvy. Všechny tyto hodnoty musí být v rozsahu 0 až 255. První 255 označuje, že je plně neprůhledné barva a druhý 255 označuje, že komponentu red je úplná intenzitou. Dva nulami znamená, že součásti zelené a modré mít intenzitou 0.  
  
 Předaný čtyři číslice (0, 0, 100, 60) <xref:System.Drawing.Graphics.FillEllipse%2A> metoda zadejte umístění a velikost ohraničující obdélník pro se třemi tečkami. Rámeček má levého horního rohu (0, 0), 100 šířka a výška 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Použití štětce k vyplnění obrazců](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
