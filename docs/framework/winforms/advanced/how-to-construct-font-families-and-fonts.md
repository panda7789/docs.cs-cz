---
title: 'Postupy: Vytváření rodin písem a písem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: d3c4b5b4293b62cfec0f8471f90be673854e9009
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590358"
---
# <a name="how-to-construct-font-families-and-fonts"></a>Postupy: Vytváření rodin písem a písem
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] písma se stejný druh písma šifry, ale různé styly seskupí do rodiny písem. Řada Arial písmo obsahuje například následující písma:  
  
- Arial standardní  
  
- Arial tučného písma  
  
- Arial kurzíva  
  
- Arial tučná kurzíva  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] používá čtyři styly formuláře rodin: pravidelných, tučné, kurzíva a Tučná kurzíva. Přídavných jmen, jako *zúžit* a *zaokrouhlí* nejsou považovány za styly; místo toho jsou součástí název rodiny. Arial úzký například je rodina písem s následující členy:  
  
- Arial úzký standardní  
  
- Arial úzký tučného písma  
  
- Arial úzký kurzíva  
  
- Arial úzký tučná kurzíva  
  
 Předtím, než můžete kreslení textu pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], je potřeba vytvořit <xref:System.Drawing.FontFamily> objektu a <xref:System.Drawing.Font> objektu. <xref:System.Drawing.FontFamily> Objekt Určuje řez písma (například Arial) a <xref:System.Drawing.Font> objekt určuje velikost, styl a jednotky.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří regulárních styl Arial písmo o velikosti 16 pixelů. V následujícím kódu, první argument předaný metodě <xref:System.Drawing.Font.%23ctor%2A> konstruktor je <xref:System.Drawing.FontFamily> objektu. Druhý argument určuje velikost písma měřenou v jednotkách identifikovaný čtvrtý argument. Třetí argument určuje styl.  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> je členem skupiny <xref:System.Drawing.GraphicsUnit> výčtu, a <xref:System.Drawing.FontStyle.Regular> je členem skupiny <xref:System.Drawing.FontStyle> výčtu.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Použití písem a textu](using-fonts-and-text.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
