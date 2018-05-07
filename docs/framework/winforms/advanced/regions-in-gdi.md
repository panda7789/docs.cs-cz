---
title: Oblasti v rozhraní GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: dc7f10571163d447802c90cd61d71b11d0e695d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="regions-in-gdi"></a>Oblasti v rozhraní GDI+
Oblast je část v oblasti výstupní zařízení. Oblasti může být jednoduchý (jeden rámeček) nebo komplexní (kombinaci mnohoúhelníky a uzavřené křivky). Následující obrázek znázorňuje dvou oblastí: jeden zkonstruován z obdélníku a dalších vytvořený z cesty.  
  
 ![Oblasti](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>Použití oblastí  
 Oblasti se často používají pro výstřižek a testování průchodu. Výstřižek zahrnuje omezení kreslení v určité oblasti zobrazované oblasti, obvykle část, kterou je třeba aktualizovat. Testování přístupů zahrnuje kontroly k určení, zda kurzor se nachází v určité oblasti obrazovky při stisknutí tlačítka myši.  
  
 Můžete vytvořit oblasti, obdélníku nebo cestu. Můžete také vytvořit komplexní oblasti kombinací existující oblasti. <xref:System.Drawing.Region> Třída poskytuje následující metody pro kombinování oblastí: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, a <xref:System.Drawing.Region.Complement%2A>.  
  
 Průnik dvou oblastí je sada všech bodů, které patří do obou oblastí. Sjednocení je sada všech bodů patřící do jeden nebo druhý nebo obou oblastí. Doplňkovým oblasti je sada všech bodů, které nejsou v oblasti. Následující obrázek znázorňuje průsečíkem a sjednocení dvou oblastí vidět na předchozím obrázku.  
  
 ![Oblasti](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A> Metoda, použije na pár oblastí, vytváří oblasti, která obsahuje všechny body, které patří do jedné oblasti nebo dalších, ale ne obojí. <xref:System.Drawing.Region.Exclude%2A> Metoda, použije na pár oblastí, vytváří oblasti, která obsahuje všechny body v první oblasti, které nejsou v druhé oblasti. Následující obrázek znázorňuje oblastí, které vyplývají z <xref:System.Drawing.Region.Xor%2A> a <xref:System.Drawing.Region.Exclude%2A> metody dvou oblastí zobrazí na začátku tohoto tématu.  
  
 ![Oblasti](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 K vyplnění oblasti, budete potřebovat <xref:System.Drawing.Graphics> objekt, <xref:System.Drawing.Brush> objekt a <xref:System.Drawing.Region> objektu. <xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.FillRegion%2A> metody a <xref:System.Drawing.Brush> objekt uloží atributy výplně, jako je například barvu nebo vzorek. Následující příklad doplní oblast plnou barvou.  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Použití oblastí](../../../../docs/framework/winforms/advanced/using-regions.md)
