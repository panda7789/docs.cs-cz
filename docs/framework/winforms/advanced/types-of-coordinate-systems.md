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
ms.openlocfilehash: ff53942cb90721d5411f99b261f90366d039e151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529750"
---
# <a name="types-of-coordinate-systems"></a>Typy souřadnicových systémů
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] používá tři souřadnice mezery: world, stránky a zařízení. Souřadnice World jsou použita k modelování konkrétní grafické world souřadnice a souřadnice, které můžete předat metody v rozhraní .NET Framework. Stránka souřadnice naleznete souřadnicový systém používán kreslicí plochy, jako jsou formuláře nebo ovládacího prvku. Souřadnice zařízení jsou souřadnice používané fyzického zařízení přitahuje, jako je obrazovky nebo list papíru. Pokud provedete volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, body, které můžete předat <xref:System.Drawing.Graphics.DrawLine%2A> metoda –`(0, 0)` a `(160, 80)`– jsou v prostoru souřadnic world. Před [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete nakreslení čáry na obrazovce, souřadnice předávat posloupnost transformace. Jeden transformace, názvem Světové transformace převede world souřadnice jiného a jiné transformace, názvem transformace stránky převede souřadnice stránky na zařízení souřadnice.  
  
## <a name="transforms-and-coordinate-systems"></a>Systémy souřadnic a transformace  
 Předpokládejme, že chcete pro práci s souřadnicový systém, který má původ v těle klientské oblasti místo levého horního rohu. Řekněme například, které chcete počátek 100 pixelů od levého okraje klientské oblasti a 50 pixelů z horní části oblasti klienta. Následující obrázek znázorňuje souřadnicový systém.  
  
 ![Systém souřadnic](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Pokud provedete volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, získání řádku vidět na následujícím obrázku.  
  
 ![Systém souřadnic](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Souřadnice z koncových bodů vaší čáry v tři souřadnice prostory jsou následující:  
  
|||  
|-|-|  
|World|(0, 0) na (160, 80)|  
|Stránka|(100, 50) na (260, 130)|  
|Zařízení|(100, 50) na (260, 130)|  
  
 Upozorňujeme, že stránka souřadnicového prostoru má původ v levém horním rohu klientské oblasti; vždy to bude v případě. Všimněte si také, že Měrná jednotka je pixelech, a proto souřadnice zařízení jsou stejné jako souřadnice stránky. Pokud nastavíte Měrná jednotka služby něco jiného než pixelů (například palce), pak budou liší od souřadnice stránky souřadnice zařízení.  
  
 Světové transformace, která se mapuje na stránce souřadnice world souřadnice, trvá v <xref:System.Drawing.Graphics.Transform%2A> vlastnost <xref:System.Drawing.Graphics> třídy. V předchozím příkladu je Světové transformace 100 jednotky překladu ve směru osy x a 50 jednotky ve směru osy y. Následující příklad ilustruje Světové transformace <xref:System.Drawing.Graphics> objektu, který používá <xref:System.Drawing.Graphics> objekt kreslení čáry vidět na předchozím obrázku:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Transformace stránky mapuje stránky souřadnice souřadnice zařízení. <xref:System.Drawing.Graphics> Třída poskytuje <xref:System.Drawing.Graphics.PageUnit%2A> a <xref:System.Drawing.Graphics.PageScale%2A> vlastnosti pro manipulaci s transformace stránky. <xref:System.Drawing.Graphics> Třída rovněž poskytuje dvě vlastnosti jen pro čtení, <xref:System.Drawing.Graphics.DpiX%2A> a <xref:System.Drawing.Graphics.DpiY%2A>, pro zkoumání vodorovného a svislého bodů na palec zobrazení zařízení.  
  
 Můžete použít <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.Graphics> třídy zadejte jednotku míry než pixelech.  
  
> [!NOTE]
>  Nelze nastavit <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.GraphicsUnit.World>, protože to není fyzické jednotky a způsobí výjimku.  
  
 Následující příklad nevykresluje řádek ze (0, 0) na (2, 1), kde je bod (2, 1) je 2 palce vpravo a 1 palec dolů z bodu (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Pokud nezadáte šířku při vytvoření pera, bude v předchozím příkladu nakreslit čáru, která je jeden palec široké. Můžete zadat šířku pera v druhý argument <xref:System.Drawing.Pen> konstruktor:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Pokud předpokládáme, že má zařízení zobrazení 96 bodů na palec ve vodorovném směru a 96 bodů na palec ve svislém směru, koncové body řádek v předchozím příkladu mají následující souřadnice do prostorů tři souřadnice:  
  
|||  
|-|-|  
|World|(0, 0) na (2, 1)|  
|Stránka|(0, 0) na (2, 1)|  
|Zařízení|(0, 0, do (192, 96)|  
  
 Upozorňujeme, že vzhledem k tomu počátek souřadnicového prostoru world v levém horním rohu klientské oblasti, souřadnice stránky jsou stejné jako souřadnice world.  
  
 Můžete kombinovat world a stránka transformace k dosažení různé efekty. Předpokládejme například, kterou chcete použít palce jako měrná jednotka služby a chcete původ systému souřadnice 2 palce od levého okraje klientské oblasti a 1/2 palce z horní části oblasti klienta. Následující příklad ilustruje world a stránka transformace z <xref:System.Drawing.Graphics> objektu a poté nakreslí řádek ze (0, 0) na (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Následující obrázek znázorňuje řádku a souřadnicový systém.  
  
 ![Systém souřadnic](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Pokud předpokládáme, že má zařízení zobrazení 96 bodů na palec ve vodorovném směru a 96 bodů na palec ve svislém směru, koncové body řádek v předchozím příkladu mají následující souřadnice do prostorů tři souřadnice:  
  
|||  
|-|-|  
|World|(0, 0) na (2, 1)|  
|Stránka|(2, 0,5) na (4, 1.5)|  
|Zařízení|(192, 48) na (384, 144)|  
  
## <a name="see-also"></a>Viz také  
 [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Maticové znázornění transformací](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
