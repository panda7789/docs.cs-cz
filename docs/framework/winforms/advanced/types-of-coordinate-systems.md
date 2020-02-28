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
ms.openlocfilehash: bbb0d4908d4a281499336d262c653d7b72f3ccdc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159803"
---
# <a name="types-of-coordinate-systems"></a>Typy souřadnicových systémů
GDI+ používá tři prostory souřadnic: World, Page a Device. Světové souřadnice jsou souřadnice používané k modelování konkrétního grafického světa a jsou souřadnicemi, které předáváte metodám v .NET Framework. Souřadnice stránky odkazují na systém souřadnic používaný plochou kreslení, jako je například formulář nebo ovládací prvek. Souřadnice zařízení jsou souřadnice používané fyzickým zařízením, které se vykresluje, jako je například obrazovka nebo list papíru. Po provedení `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`volání jsou body, které předáte metodě <xref:System.Drawing.Graphics.DrawLine%2A> –`(0, 0)` a `(160, 80)`, umístěny v prostoru souřadnic World. Předtím, než může rozhraní GDI+ vykreslit čáru na obrazovce, přejdou souřadnice posloupnosti transformací. Jedna transformace, nazývaná světová transformace, převede Světové souřadnice na souřadnice stránky a jinou transformaci, která se nazývá transformace stránky, převede souřadnice stránky na souřadnice zařízení.  
  
## <a name="transforms-and-coordinate-systems"></a>Transformace a koordinace systémů  
 Předpokládejme, že chcete pracovat se systémovou souřadnicí, která má svůj původ v těle oblasti klienta, nikoli v levém horním rohu. Řekněme například, že chcete, aby počátek byl 100 pixelů od levého okraje klientské oblasti a 50 pixelů od horní části klientské oblasti. Následující obrázek znázorňuje systém souřadnic.  
  
 ![Systém souřadnic](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Po provedení volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`získáte řádek na následujícím obrázku.  
  
 ![Systém souřadnic](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Souřadnice koncových bodů na řádku ve třech souřadnicových prostorech jsou následující:  
  
|||  
|-|-|  
|World|(0, 0) až (160, 80)|  
|Stránka|(100, 50) až (260, 130)|  
|Zařízení|(100, 50) až (260, 130)|  
  
 Všimněte si, že prostor souřadnic stránky má svůj počátek v levém horním rohu klientské oblasti. to bude mít vždycky tento případ. Všimněte si také, že vzhledem k tomu, že jednotka míry je pixel, jsou souřadnice zařízení stejné jako souřadnice stránky. Pokud nastavíte měrnou jednotku na jinou hodnotu než pixely (například palce), souřadnice zařízení se budou lišit od souřadnic stránky.  
  
 Transformace světa, která mapuje souřadnice světa na souřadnice stránky, je uložena ve vlastnosti <xref:System.Drawing.Graphics.Transform%2A> třídy <xref:System.Drawing.Graphics>. V předchozím příkladu je transformace světa převodem jednotek 100 ve směru x a 50 jednotek ve směru y. Následující příklad nastaví světovou transformaci objektu <xref:System.Drawing.Graphics> a poté pomocí tohoto objektu <xref:System.Drawing.Graphics> vykreslí řádek zobrazený na předchozím obrázku:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Transformace stránky mapuje souřadnice stránky na souřadnice zařízení. Třída <xref:System.Drawing.Graphics> poskytuje vlastnosti <xref:System.Drawing.Graphics.PageUnit%2A> a <xref:System.Drawing.Graphics.PageScale%2A> pro manipulaci s transformací stránky. Třída <xref:System.Drawing.Graphics> také poskytuje dvě vlastnosti jen pro čtení, <xref:System.Drawing.Graphics.DpiX%2A> a <xref:System.Drawing.Graphics.DpiY%2A>pro zkoumání vodorovných a svislých bodů na palec zobrazovacího zařízení.  
  
 Vlastnost <xref:System.Drawing.Graphics.PageUnit%2A> třídy <xref:System.Drawing.Graphics> můžete použít k určení měrné jednotky, která je jiná než pixel.  
  
> [!NOTE]
> Vlastnost <xref:System.Drawing.Graphics.PageUnit%2A> nelze nastavit na hodnotu <xref:System.Drawing.GraphicsUnit.World>, protože se nejedná o fyzickou jednotku a vyvolá výjimku.  
  
 Následující příklad Kreslí čáru od (0, 0) do (2, 1), kde je bod (2, 1) 2 palců vpravo a 1 palec dolů od bodu (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> Pokud při sestavování pera nezadáte šířku pera, v předchozím příkladu se nakreslí čára, která je o jednu palce široké. Šířku pera můžete zadat v druhém argumentu <xref:System.Drawing.Pen> konstruktoru:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Pokud předpokládáme, že zobrazovací zařízení má 96 bodů na palec v horizontálním směru a 96 bodů na palec ve svislém směru, koncových bodů v předchozím příkladu mají následující souřadnice ve třech souřadnicových prostorech:  
  
|||  
|-|-|  
|World|(0, 0) až (2, 1)|  
|Stránka|(0, 0) až (2, 1)|  
|Zařízení|(0, 0) až (192, 96)|  
  
 Všimněte si, že vzhledem k tomu, že počátek prostoru souřadnic světa je v levém horním rohu klientské oblasti, souřadnice stránky jsou stejné jako u světových souřadnic.  
  
 K dosažení celé řady efektů můžete kombinovat svět a transformace stránek. Předpokládejme například, že chcete použít palce jako měrnou jednotku a chcete, aby byl počátek souřadnicového systému 2 palce od levého okraje oblasti klienta a 1/2 palce od horní části klientské oblasti. Následující příklad nastaví World a Page Transformers objektu <xref:System.Drawing.Graphics> a potom nakreslí čáru od (0, 0) do (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Následující ilustrace znázorňuje systém řádku a souřadnic.  
  
 ![Systém souřadnic](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Pokud předpokládáme, že zobrazovací zařízení má 96 bodů na palec v horizontálním směru a 96 bodů na palec ve svislém směru, koncových bodů v předchozím příkladu mají následující souřadnice ve třech souřadnicových prostorech:  
  
|||  
|-|-|  
|World|(0, 0) až (2, 1)|  
|Stránka|(2, 0,5) až (4, 1,5)|  
|Zařízení|(192, 48) až (384, 144)|  
  
## <a name="see-also"></a>Viz také

- [Systém souřadnic a transformace](coordinate-systems-and-transformations.md)
- [Maticové znázornění transformací](matrix-representation-of-transformations.md)
