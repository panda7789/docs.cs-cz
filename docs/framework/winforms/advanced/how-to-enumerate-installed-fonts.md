---
title: 'Postupy: Výčet instalovaných písem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653740"
---
# <a name="how-to-enumerate-installed-fonts"></a>Postupy: Výčet instalovaných písem
<xref:System.Drawing.Text.InstalledFontCollection> Třída dědí z <xref:System.Drawing.Text.FontCollection> abstraktní základní třída. Můžete použít <xref:System.Drawing.Text.InstalledFontCollection> objekt výčet písem v počítači nainstalována. <xref:System.Drawing.Text.FontCollection.Families%2A> Vlastnost <xref:System.Drawing.Text.InstalledFontCollection> objektu je pole <xref:System.Drawing.FontFamily> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad zobrazí seznam názvů rodin písem v počítači nainstalována. Kód načte <xref:System.Drawing.FontFamily.Name%2A> vlastnosti každého <xref:System.Drawing.FontFamily> objekt v poli vrácené <xref:System.Drawing.Text.FontCollection.Families%2A> vlastnost. Protože jsou načteny názvy rodiny, jsou zřetězeny do formuláře čárkou oddělený seznam. Pak bude <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třídy kreslení v obdélníku seznam oddělený čárkami.  
  
 Pokud spustíte příklad kódu, výstup bude podobný tomu je znázorněno na následujícím obrázku:  
  
 ![Snímek obrazovky zobrazující rodin písem nainstalované.](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>. Kromě toho byste měli importovat <xref:System.Drawing.Text> oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- [Použití písem a textu](using-fonts-and-text.md)
