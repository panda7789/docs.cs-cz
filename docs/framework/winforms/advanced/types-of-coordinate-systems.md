---
title: Typy souřadnicových systémů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: 765df4bcd3cef83e624ad8b11676696b95f7d035
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089299"
---
# <a name="types-of-coordinate-systems"></a>Typy souřadnicových systémů
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] používá tři souřadnicových prostorech: world, stránky a zařízení. Světové souřadnice jsou souřadnice používají k modelování zvláštního grafického světa a souřadnice, které můžete předat do metody v rozhraní .NET Framework. Souřadnice stránky najdete souřadnicový systém používá povrchem výkresu, jako je například formulář nebo ovládací prvek. Souřadnice zařízení jsou souřadnice použít fyzické zařízení, které je cílem vykreslování, jako je obrazovka nebo list papíru. Když nastavíte volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, body, které můžete předat <xref:System.Drawing.Graphics.DrawLine%2A> metoda –`(0, 0)` a `(160, 80)`– jsou v souřadnicového prostoru světa. Před [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete na obrazovce nakreslí čáru, souřadnice předávání sekvence transformací. Jedna transformace, volá Světové transformace převede Světové souřadnice na souřadnice stránky, a jinou transformaci, volá transformace stránky převede souřadnice stránky na souřadnice zařízení.  
  
## <a name="transforms-and-coordinate-systems"></a>Transformace a souřadnicových systémů  
 Předpokládejme, že budete chtít pracovat s souřadnicový systém, který má původ v těle klientské oblasti spíše než levém horním rohu. Řekněme například, že chcete, aby původu 100 pixelů od levého okraje oblasti klienta a 50 pixelů od horního okraje oblasti klienta. Následující obrázek znázorňuje souřadnicový systém.  
  
 ![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Když nastavíte volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, zobrazí se řádek je znázorněno na následujícím obrázku.  
  
 ![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Souřadnice z koncových bodů vaší řádku v tři souřadnicových prostorech jsou následující:  
  
|||  
|-|-|  
|World|(0, 0) na (160, 80)|  
|Stránka|(100, 50) na (260, 130)|  
|Zařízení|(100, 50) na (260, 130)|  
  
 Mějte na paměti, že má souřadnicového prostoru stránku původu v levém horním rohu oblasti klienta; to bude vždy probíhat případu. Všimněte si také, protože je jednotka měření je pixel, souřadnice zařízení jsou stejné jako souřadnice stránky. Pokud nastavíte měrnou jednotku na něco jiného než pixelů (například palce), bude se liší od souřadnice stránky souřadnice zařízení.  
  
 Světové transformace, která mapuje Světové souřadnice na souřadnice stránky, se nachází v <xref:System.Drawing.Graphics.Transform%2A> vlastnost <xref:System.Drawing.Graphics> třídy. V předchozím příkladu je Světové transformace 100 jednotek překladu ve směru osy x a 50 jednotek ve směru osy y. Následující příklad nastaví Světové transformace <xref:System.Drawing.Graphics> objekt a potom použije <xref:System.Drawing.Graphics> objekt nakreslení čáry je vidět na předchozím obrázku:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Transformace stránky mapuje na souřadnice zařízení souřadnice stránky. <xref:System.Drawing.Graphics> Třída poskytuje <xref:System.Drawing.Graphics.PageUnit%2A> a <xref:System.Drawing.Graphics.PageScale%2A> vlastnosti pro manipulaci s transformace stránky. <xref:System.Drawing.Graphics> Třída rovněž poskytuje dvě vlastnosti jen pro čtení, <xref:System.Drawing.Graphics.DpiX%2A> a <xref:System.Drawing.Graphics.DpiY%2A>, zkoumat vodorovného a svislého bodů na palec zobrazovacího zařízení.  
  
 Můžete použít <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.Graphics> tak, aby určovala jednotka měření, než je pixel.  
  
> [!NOTE]
>  Nelze nastavit <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.GraphicsUnit.World>, protože to není fyzické jednotky a způsobí výjimku.  
  
 Následující příklad nakreslí čáru z (0, 0) na (2, 1), kde je bod (2, 1) 2 palce napravo a 1 palce dolů z bodu (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Pokud nezadáte Šířka pera při konstrukci pera, bude v předchozím příkladu nakreslit čáru, která je jednu palec široké. Můžete určit šířku pera v druhý argument <xref:System.Drawing.Pen> konstruktor:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Pokud předpokládáme, že zařízení má 96 přichycováním k pixelům ve vodorovném směru a 96 přichycováním k pixelům ve svislém směru, koncové body čáry v předchozím příkladu mají tyto souřadnice v tři souřadnice mezery:  
  
|||  
|-|-|  
|World|(0, 0) na (2, 1)|  
|Stránka|(0, 0) na (2, 1)|  
|Zařízení|(0, 0, do (192, 96)|  
  
 Všimněte si, že v levém horním rohu klientské oblasti je počátek souřadnicového prostoru světa, souřadnice stránky jsou stejné jako Světové souřadnice.  
  
 Můžete kombinovat transformace světa a stránky k dosažení různé účinky. Předpokládejme například, kterou chcete použít jako jednotka měření palců a chcete počátek souřadnic systému 2 palcích od levého okraje oblasti klienta a 1/2 palce od horního okraje oblasti klienta. Následující příklad nastaví transformace světa a stránka <xref:System.Drawing.Graphics> objekt a potom nakreslí čáru z (0, 0) na (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Následující obrázek znázorňuje řádku a systém souřadnic.  
  
 ![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Pokud předpokládáme, že zařízení má 96 přichycováním k pixelům ve vodorovném směru a 96 přichycováním k pixelům ve svislém směru, koncové body čáry v předchozím příkladu mají tyto souřadnice v tři souřadnice mezery:  
  
|||  
|-|-|  
|World|(0, 0) na (2, 1)|  
|Stránka|(2, 0,5) na (4, 1.5)|  
|Zařízení|(192, 48) na (384, 144)|  
  
## <a name="see-also"></a>Viz také:

- [Systém souřadnic a transformace](coordinate-systems-and-transformations.md)
- [Maticové znázornění transformací](matrix-representation-of-transformations.md)
