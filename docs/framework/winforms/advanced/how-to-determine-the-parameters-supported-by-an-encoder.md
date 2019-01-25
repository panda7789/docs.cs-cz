---
title: 'Postupy: Určuje parametry podporuje kodéru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 56b78a0cdfcb9ac8e3a7dbc12527fcc59f0524fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723404"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>Postupy: Určuje parametry podporuje kodéru
Můžete upravit parametry image, například úroveň kvality a provádí kompresi, ale musíte vědět, jaké parametry jsou podporovány kodér danou image. <xref:System.Drawing.Image> Třída poskytuje <xref:System.Drawing.Image.GetEncoderParameterList%2A> metodu tak, aby bylo možné určit, které image parametry jsou podporovány pro konkrétní kodér. Zadejte kodér s identifikátorem GUID. <xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda vrátí pole <xref:System.Drawing.Imaging.EncoderParameter> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vypíše podporovaných parametrů pro kodér JPEG. Pomocí seznamu kategorií parametr a přidružené identifikátory GUID <xref:System.Drawing.Imaging.Encoder> přehledu třídy k určení kategorie každého parametru.  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace modelu Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vypsání seznamu instalovaných kodérů](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [Typy rastrových obrázků](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
- [Použití kodérů a dekodérů ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
