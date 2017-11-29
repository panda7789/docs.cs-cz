---
title: "Postupy: Vypsání seznamu instalovaných dekodérů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17cbdebfa6cbb0cacacd923de4bd22125c812938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-decoders"></a>Postupy: Vypsání seznamu instalovaných dekodérů
Můžete k zobrazení seznamu dekodérů bitové kopie k dispozici v počítačích k určení, jestli vaše aplikace může číst konkrétní TIFF. <xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statických metod, aby mohla určit, která image dekódovací moduly jsou k dispozici. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu Vypíše seznam nainstalovaných dekodérů a jejich hodnoty vlastností.  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vypsání seznamu instalovaných kodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Použití kodérů a dekodérů ve spravovaném GDI +](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
