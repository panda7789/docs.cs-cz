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
ms.openlocfilehash: 492930b7d8a47db478c8fa0f282cb5f491e144ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708454"
---
# <a name="how-to-list-installed-encoders"></a>Postupy: Vypsání seznamu instalovaných kodérů
Můžete chtít seznamu kodérů image dostupných na počítači, k určení, jestli vaše aplikace můžete uložit do formátu souboru konkrétní image. <xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statické metody tak, aby bylo možné určit, která image kodérů jsou k dispozici. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu Vypíše seznam nainstalovaných kodérů a jejich hodnot vlastností.  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace modelu Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vypsání seznamu instalovaných dekodérů](how-to-list-installed-decoders.md)
- [Použití kodérů a dekodérů ve spravovaném GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
