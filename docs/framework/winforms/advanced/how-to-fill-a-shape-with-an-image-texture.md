---
title: 'Postupy: Vyplnění obrazce pomocí textury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 099bc9f5359f19439f308f28a6766d470956daea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177317"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Postupy: Vyplnění obrazce pomocí textury
Můžete vyplnit zavřeného tvaru textury s použitím <xref:System.Drawing.Image> třídy a <xref:System.Drawing.TextureBrush> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkopíruje elipsu s obrázkem. Vytvoří kód <xref:System.Drawing.Image> objektu a předá adresu, která <xref:System.Drawing.Image> jako argument pro objekt <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktoru. Třetí příkaz změní velikost obrázku, a čtvrtý příkaz vyplní elipsu s opakovaného kopírování obrazu se změněnou velikostí.  
  
 V následujícím kódu <xref:System.Drawing.TextureBrush.Transform%2A> vlastnost obsahuje transformace, která je u obrázku před jeho vykreslení. Předpokládejme, že původní obrázek obsahuje 640 pixelů šířku a výšku 480 pixelů. Transformace zmenší bitovou kopii na 75 × 75 nastavením hodnoty vodorovného a svislého škálování.  
  
> [!NOTE]
>  V následujícím příkladu velikost obrázku je 75 × 75 a velikosti elipsy je 150 × 250. Vzhledem k tomu, že na obrázku je menší než elipsy, který je naplnění, se třemi tečkami je rozložen formou dlaždic s imagí. Dělení na bloky znamená, že obrázek se opakuje vodorovně a svisle do hranice obrazce je dosaženo. Další informace o dělení najdete v tématu [jak: Dlaždicové vyplnění obrazce pomocí obrázku](how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Použití štětce k vyplnění obrazců](using-a-brush-to-fill-shapes.md)
