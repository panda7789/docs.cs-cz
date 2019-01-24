---
title: 'Postupy: Vypsání seznamu instalovaných dekodérů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: 3d24eadca23aa6da4a8557cc2db3189b6e232e78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605200"
---
# <a name="how-to-list-installed-decoders"></a>Postupy: Vypsání seznamu instalovaných dekodérů
Můžete chtít seznamu dekodérů bitové kopie k dispozici v počítači, chcete-li zjistit, jestli vaše aplikace může číst formátu souboru konkrétní image. <xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statické metody tak, aby bylo možné určit, která image dekodérů jsou k dispozici. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu Vypíše seznam nainstalovaných dekodérů a jejich hodnot vlastností.  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace modelu Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vypsání seznamu instalovaných kodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [Použití kodérů a dekodérů ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
