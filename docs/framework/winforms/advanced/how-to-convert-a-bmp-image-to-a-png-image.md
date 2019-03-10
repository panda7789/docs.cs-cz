---
title: 'Postupy: Převod obrázku Bpm na obrázek PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: f8636bea120aee86c795b4196415145a484e5772
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724996"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Postupy: Převod obrázku Bpm na obrázek PNG
Často budete chtít převést z jedné image soubor formátu do jiného. Tento převod může snadno provést zavoláním <xref:System.Drawing.Image.Save%2A> metodu <xref:System.Drawing.Image> třídy a zadáte <xref:System.Drawing.Imaging.ImageFormat> pro formát souborů požadovanou image.  
  
## <a name="example"></a>Příklad  
 Následující příklad načte obrázku Bpm na obrázek z typu a uloží obrázek ve formátu PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace modelu Windows Forms.  
  
-   Odkaz na `System.Drawing.Imaging` oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vypsání seznamu instalovaných kodérů](how-to-list-installed-encoders.md)
- [Použití kodérů a dekodérů ve spravovaném GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
- [Typy rastrových obrázků](types-of-bitmaps.md)
