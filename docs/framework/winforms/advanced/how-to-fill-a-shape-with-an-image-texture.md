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
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911679"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Postupy: Vyplnění obrazce pomocí textury
Uzavřený tvar můžete vyplnit texturou pomocí <xref:System.Drawing.Image> třídy <xref:System.Drawing.TextureBrush> a třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vyplní elipsu obrázkem. Kód vytvoří <xref:System.Drawing.Image> objekt a poté předá adresu <xref:System.Drawing.Image> tohoto objektu <xref:System.Drawing.TextureBrush.%23ctor%2A> jako argument konstruktoru. Třetí příkaz škáluje obrázek a čtvrtý příkaz vyplní elipsu opakovanými kopiemi obrázku s měřítkem.  
  
 V následujícím kódu <xref:System.Drawing.TextureBrush.Transform%2A> vlastnost obsahuje transformaci, která je použita na obrázek před vykreslením. Předpokládat, že původní obrázek má šířku 640 pixelů a výšku 480 pixelů. Transformace zmenší obrázek na 75 × 75 nastavením hodnot horizontálního a svislého měřítka.  
  
> [!NOTE]
> V následujícím příkladu je velikost obrázku 75 × 75 a velikost elipsy je 150 × 250. Vzhledem k tomu, že je obrázek menší než elipsa, která je vyplňuje, je elipsa v dlaždici s obrázkem. Dláždění znamená, že se obrázek opakuje vodorovně a svisle, dokud nedosáhne hranice tvaru. Další informace o dlaždicích naleznete v [tématu How to: Dlaždici tvar s obrázkem](how-to-tile-a-shape-with-an-image.md)  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což <xref:System.Windows.Forms.Control.Paint> je parametr obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Použití štětce k vyplnění obrazců](using-a-brush-to-fill-shapes.md)
