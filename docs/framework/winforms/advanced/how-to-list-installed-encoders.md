---
title: 'Postupy: Vypsání seznamu instalovaných kodérů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: c5019a349b4f3c881190241042cecc6c4c571950
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605653"
---
# <a name="how-to-list-installed-encoders"></a>Postupy: Vypsání seznamu instalovaných kodérů
Můžete chtít seznamu kodérů image dostupných na počítači, k určení, jestli vaše aplikace můžete uložit do formátu souboru konkrétní image. <xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statické metody tak, aby bylo možné určit, která image kodérů jsou k dispozici. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu Vypíše seznam nainstalovaných kodérů a jejich hodnot vlastností.  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace modelu Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vypsání seznamu instalovaných dekodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)
- [Použití kodérů a dekodérů ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
