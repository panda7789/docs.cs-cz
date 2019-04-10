---
title: 'Postupy: Určení parametrů podporovaných kodérem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 2626eee239d9876125340dd133c5a9b3e45c3d7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204572"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>Postupy: Určení parametrů podporovaných kodérem
Můžete upravit parametry image, například úroveň kvality a provádí kompresi, ale musíte vědět, jaké parametry jsou podporovány kodér danou image. <xref:System.Drawing.Image> Třída poskytuje <xref:System.Drawing.Image.GetEncoderParameterList%2A> metodu tak, aby bylo možné určit, které image parametry jsou podporovány pro konkrétní kodér. Zadejte kodér s identifikátorem GUID. <xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda vrátí pole <xref:System.Drawing.Imaging.EncoderParameter> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vypíše podporovaných parametrů pro kodér JPEG. Pomocí seznamu kategorií parametr a přidružené identifikátory GUID <xref:System.Drawing.Imaging.Encoder> přehledu třídy k určení kategorie každého parametru.  
  
 [!code-csharp[UsingImageEncodersDecoders#3](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Aplikace modelu Windows Forms.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vypsání seznamu instalovaných kodérů](how-to-list-installed-encoders.md)
- [Typy rastrových obrázků](types-of-bitmaps.md)
- [Použití kodérů a dekodérů ve spravovaném GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
