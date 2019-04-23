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
ms.openlocfilehash: 92f27399cce9e03a4679c8a34fbdafcf28c32252
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155009"
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
