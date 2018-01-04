---
title: "Postupy: Určení parametrů podporovaných kodérem"
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
helpviewer_keywords: encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3304adc9ab22d12905bd2a6c3739d909387d82cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>Postupy: Určení parametrů podporovaných kodérem
Můžete upravit parametry bitové kopie, například úrovně kvality a komprese, ale musíte vědět, jaké parametry jsou podporovány kodér danou bitovou kopii. <xref:System.Drawing.Image> Třída poskytuje <xref:System.Drawing.Image.GetEncoderParameterList%2A> metoda, aby mohla určit, které parametry bitové kopie jsou podporovány pro konkrétní kodér. Kodér zadáte s identifikátorem GUID. <xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda vrátí pole <xref:System.Drawing.Imaging.EncoderParameter> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu výstupy podporované parametry pro kodér JPEG. Použijte seznam kategorií parametr a přidružené identifikátory GUID v <xref:System.Drawing.Imaging.Encoder> přehledu třídy k určení kategorie pro jednotlivé parametry.  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vypsání seznamu instalovaných kodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Typy rastrových obrázků](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [Použití kodérů a dekodérů ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
