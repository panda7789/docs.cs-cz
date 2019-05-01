---
title: 'Postupy: Použití matice barev k transformaci jedné barvy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 78fc498b0689026fb74ec0c422948c1879495560
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954807"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>Postupy: Použití matice barev k transformaci jedné barvy
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulaci s obrázky. <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> objekty ukládání barvu každého obrazového bodu jako 32bitová čísla: 8 bity pro červená, zelená, modrá a alfa. Každý ze čtyř komponent je číslo od 0 do 255, kde 0 představuje žádné intenzity a 255 představující plné intenzity. Hodnota alfa Určuje průhlednost barvy: 0 je zcela transparentní, a je úplně neprůhledná 255.  
  
 Barva vektor je 4-n-tice formuláře (červená, zelená, modrá, alfa). Například vektor barvy (0, 255, 0, 255) představuje neprůhledné barvu nemá žádné červená a modrá, ale má zelená při plné intenzity.  
  
 Jiné konvence pro zastoupení barvy používá číslo 1 pro plné intenzity. Pomocí této konvenci, barva je popsáno v předchozím odstavci by být reprezentována vektor (0, 1, 0, 1). [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] používá konvenci 1 jako plné intenzity při provádění transformace barev.  
  
 Lineární transformace (otočení, škálování a podobně) můžete použít barvu vektory vynásobením vektory barva podle matice 4 x 4. Matice 4 x 4 však nelze používat pro překlad (nelineárních). Pokud chcete přidat fiktivní páté souřadnice (například číslo 1) ke každému barva vektorů, můžete použít libovolnou kombinaci lineární transformace a překlady matice 5 × 5. Transformace skládající se z lineární transformace, za nímž následuje překlad se nazývá afinní transformace.  
  
 Předpokládejme například, že chcete začít s barvou (0.2, 0.0, 0.4, 1.0) a platí následující transformace:  
  
1. Double hodnota červené  
  
2. Přidání do komponenty červené, zelené a modré 0.2  
  
 Následující násobení matic provede pár transformace v uvedeném pořadí.  
  
 ![Přebarvení](./media/recoloring01.gif "recoloring01")  
  
 Prvky matice barev jsou indexovány pomocí řádku a potom sloupce (počítáno od nuly). Například, položku pátý řádek a třetí sloupec matice M udávají M [4] [2].  
  
 5 × 5 jednotkovou matici (viz následující obrázek) má 1s na diagonální a 0s všude, kde jiný. Pokud je barva vektor vynásobit jednotkovou matici, barva vektoru se nezmění. Pohodlný způsob, jak tvoří matice barev transformace je začít s jednotkovou matici a proveďte malou změnu, která vytváří svou požadovanou transformaci.  
  
 ![Přebarvení](./media/recoloring02.gif "recoloring02")  
  
 Podrobnější diskuzi o matice a transformace, najdete v článku [systém souřadnic a transformace](coordinate-systems-and-transformations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá image, která je všechny jednu barvu (0.2, 0.0, 0.4, 1.0) a platí transformace je popsáno v předchozích odstavcích.  
  
 Následující obrázek znázorňuje původní obrázek na levé straně a transformovaná image na pravé straně.  
  
 ![Colors](./media/colortrans1.png "colortrans1")  
  
 Kód v následujícím příkladu používá následující kroky provést přebarvení:  
  
1. Inicializace <xref:System.Drawing.Imaging.ColorMatrix> objektu.  
  
2. Vytvoření <xref:System.Drawing.Imaging.ImageAttributes> objektu a předejte <xref:System.Drawing.Imaging.ColorMatrix> objektu <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu.  
  
3. Předání <xref:System.Drawing.Imaging.ImageAttributes> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Přebarvení obrázků](recoloring-images.md)
- [Systém souřadnic a transformace](coordinate-systems-and-transformations.md)
