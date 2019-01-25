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
ms.openlocfilehash: ae4931a464421639112c8f369bd27a45550fe7f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708269"
---
# <a name="regions-in-gdi"></a>Oblasti v rozhraní GDI+
Oblast je část oblasti zobrazení výstupního zařízení. Oblasti mohou být jednoduché (jeden obdélník) nebo komplexní (kombinace mnohoúhelníků a uzavřené křivky). Následující obrázek znázorňuje dvě oblasti: jeden z obdélník, který je druhou vytvářejí na základě cesty.  
  
 ![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>Použití oblastí  
 Oblasti se často používají pro oříznutí a testování průchodu. Výstřižek zahrnuje omezení kreslení v určité oblasti zobrazované oblasti, obvykle část, kterou je potřeba aktualizovat. Přístupů testování zahrnuje kontroly k určení, zda ukazatel je v určité oblasti obrazovky, když se stiskne tlačítko myši.  
  
 Můžete vytvořit oblasti, obdélníku nebo cestu. Můžete také vytvořit komplexní oblasti kombinací stávajících oblastí. <xref:System.Drawing.Region> Třída poskytuje následující metody pro kombinování oblastí: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, a <xref:System.Drawing.Region.Complement%2A>.  
  
 Průnik dvou oblastech je sada všech bodů, které patří do obou oblastech. Sjednocení je sada všech bodů, které patří do jedné nebo druhé nebo obou oblastech. Doplněk oblast je sada všech bodů, které nejsou v oblasti. Následující obrázek znázorňuje průniku a sjednocení dvou oblastech je znázorněno na předchozím obrázku.  
  
 ![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A> Metoda použitá pro dvojice oblasti, vytvoří oblast, která obsahuje všechny body, které patří do jedné oblasti nebo druhé, ale ne obojí. <xref:System.Drawing.Region.Exclude%2A> Metoda použitá pro dvojice oblasti, vytvoří oblast, která obsahuje všechny body v první oblasti, které nejsou v druhé oblasti. Následující obrázek znázorňuje oblastí, které jsou výsledkem použití <xref:System.Drawing.Region.Xor%2A> a <xref:System.Drawing.Region.Exclude%2A> metody do dvou oblastí, které jsou uvedené na začátku tohoto tématu.  
  
 ![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 K vyplnění oblasti, je nutné <xref:System.Drawing.Graphics> objektu, <xref:System.Drawing.Brush> objektu a <xref:System.Drawing.Region> objektu. <xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.FillRegion%2A> metody a <xref:System.Drawing.Brush> ukládá atributy výplň, například barvu nebo vzorek. Následující příklad zkopíruje oblasti plnou barvou.  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Použití oblastí](../../../../docs/framework/winforms/advanced/using-regions.md)
