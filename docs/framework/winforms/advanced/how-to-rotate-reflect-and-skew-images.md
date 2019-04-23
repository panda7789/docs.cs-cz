---
title: 'Postupy: Otáčení, převrácení a zkosení obrázků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 505028c491228ffdf9c11d0c71dcd5e1afdc5103
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59114039"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Postupy: Otáčení, převrácení a zkosení obrázků
Můžete otáčení, převrácení a zkosení obrázku tak, že určíte cílové body pro levého horního, pravého horního a levého dolního rohu původní bitové kopie. Tři cílovými body určit afinní transformace, která mapuje původní obrázek obdélníkové se z něj rovnoběžník.  
  
## <a name="example"></a>Příklad  
 Předpokládejme například, že původní bitové kopie je obdélník se v levém horním rohu (0, 0), v pravém horním rohu (100, 0) a v levém dolním rohu (0, 50). Nyní předpokládejme, že můžete namapovat tyto tři odkazuje na cílové body následujícím způsobem.  
  
|Původní bod|Cílový bod|  
|--------------------|-----------------------|  
|Levý horní (0, 0)|(200, 20)|  
|Upper-right (100, 0)|(110, 100)|  
|Levém (0, 50)|(250, 30)|  
  
 Následující obrázek znázorňuje původní image a image, namapované rovnoběžník. Původní bitové kopie má byla zkosený, projeví, otáčet a přeložit. Osa x podél horního okraje původní bitové kopie je namapována na řádek, který prochází (200, 20) a (110, 100). Osa y podél levého okraje původní bitové kopie je namapována na řádek, který prochází (200, 20) a (250, 30).  
  
 ![Původní image a image, namapované rovnoběžník.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-illustration.gif)  
  
 Následující obrázek znázorňuje podobné transformaci u photographic obrázku:  
  
 ![Obrázek horolezec a obrázek namapované rovnoběžník.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-photo.png)  
  
 Podobně jako transformací do metasouboru naleznete na následujícím obrázku:  
  
 ![Obrázek tvary a text a, která mapuje rovnoběžník.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-metafile.png)  
  
 Následující příklad vytvoří Image je znázorněno na prvním obrázku.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nezapomeňte nahradit `Stripes.bmp` cestou k obrázku, který je platný v systému.  
  
## <a name="see-also"></a>Viz také:

- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
