---
title: Globální a místní transformace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: fc23478cc4aaa51af3ff15bcc3c63590e7a8dcb2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630876"
---
# <a name="global-and-local-transformations"></a>Globální a místní transformace
Globální transformace je transformace, která se vztahuje na všechny položky vykreslené danou <xref:System.Drawing.Graphics> objektu. Naproti tomu místní transformace je transformace, která se vztahují k určité položce chcete kreslit.  
  
## <a name="global-transformations"></a>Globální transformace  
 Vytvoření globální transformace, sestavit <xref:System.Drawing.Graphics> objektu a pak pracuje s jeho <xref:System.Drawing.Graphics.Transform%2A> vlastnost. <xref:System.Drawing.Graphics.Transform%2A> Je vlastnost <xref:System.Drawing.Drawing2D.Matrix> objektu, takže může obsahovat libovolnou posloupností afinní transformace. Transformace uložené v <xref:System.Drawing.Graphics.Transform%2A> vlastnost se nazývá Světové transformace. <xref:System.Drawing.Graphics> Třída poskytuje několik metod pro vytváření složených Světové transformace: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, a <xref:System.Drawing.Graphics.TranslateTransform%2A>. Následující příklad nakreslí elipsu dvakrát: jednou před vytvořením Světové transformace a jednou po. Transformace nejprve škáluje faktorem 0,5 ve směru osy y, pak přeloží 50 jednotek ve směru osy x a potom otočí 30 stupňů.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Následující obrázek znázorňuje matricí součástí transformace.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  V předchozím příkladu je na tři tečky otočit o původu souřadnicový systém, který je v levém horním rohu klientské oblasti. To vytvoří jiné výsledky než otočením elipsa o vlastní center.  
  
## <a name="local-transformations"></a>Místní transformace  
 Místní transformace platí pro konkrétní položky chcete kreslit. Například <xref:System.Drawing.Drawing2D.GraphicsPath> má objekt <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> metodu, která umožňuje převést datové body dané cesty. Následující příklad nakreslí obdélník se žádné transformace a cestu transformace otočení. (Předpokládejme, že neexistuje žádná Světové transformace).  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Můžete kombinovat Světové transformace s místní transformací pro dosažení různé výsledky. Můžete například použít Světové transformace revidování systém souřadnic a místní transformace použít otočit a změnit velikost objektů vykreslen na nový systém souřadnic.  
  
 Předpokládejme, že chcete souřadnicový systém, který má jeho původu 200 pixelů od levého okraje oblasti klienta a 150 pixelů od horního okraje oblasti klienta. Kromě toho se předpokládá, který má být pixel, s osou x odkazuje na pravé straně a osy y míří nahoru měrnou jednotku. Výchozí souřadnicový systém má osy y směřující dolů, takže je potřeba provést reflexe vodorovné ose. Následující obrázek znázorňuje přehled těchto reflexe.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 V dalším kroku se předpokládá, že je potřeba provést 200 jednotkami překladu napravo a 150 jednotky dolů.  
  
 Následující příklad vytvoří souřadnicový systém právě popsanou nastavením Světové transformace <xref:System.Drawing.Graphics> objektu.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Následující kód (umístěné na konci předchozího příkladu) vytvoří cestu, která se skládá z jedné obdélníku s jeho levého dolního rohu na počátek nový systém souřadnic. Obdélník zaplněný jednou s žádné místní transformace a posléze s místní transformace. Místní transformace se skládá z horizontální škálování faktorem 2, za nímž následuje otočení kolem osy 30stupňů.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Následující obrázek znázorňuje nový systém souřadnic a těmito dvěma obdélníky.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Viz také:
- [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
- [Použití transformací ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
