---
title: Maticové znázornění transformací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
ms.openlocfilehash: 4c840d8a5abc89493bc684526ce76d34307f4ba1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="matrix-representation-of-transformations"></a>Maticové znázornění transformací
M x n matice je sady čísel uspořádané m řádků a sloupců n. Následující obrázek znázorňuje několik matice.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Přidáním jednotlivé elementy můžete přidat dvěma matic stejnou velikost. Následující obrázek znázorňuje dva příklady, přidání matice.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 M x n matice může násobí hodnotou matici p n × a výsledkem je m × p matice. Počet sloupců v první matice musí být stejný jako počet řádků v druhé matici. Například můžete matice 4 x 2 vynásobeny 2 × 3 matice k vytvoření matice 4 x 3.  
  
 Body v rovině a řádků a sloupců matice může považovat za vektory. Například (2, 5) je vektor s dvě komponenty a (3, 7, 1) je vektor s tři součásti. Tečka součin dvou vektory je definován následujícím způsobem:  
  
 (a, b) • (c, d) = ac + bd  
  
 (a, b, c) • (d, e, f) = ad + být + CR  
  
 Například tečkou produkt (2, 3) a (5, 4) je (2)(5) + (3)(4) = 22. Produkt tečkou (2, 5, 1) a (4, 3, 1) je (2)(4) + (5)(3) + (1)(1) = 24. Všimněte si, že tečkou součin dvou vektory čísla, který není jiným způsobem. Všimněte si také tečkou produktu můžete vypočítat, pouze v případě, že dva vektory mít stejný počet součástí.  
  
 Umožní A(i, j) být položka v matici A v i-tým řádků a sloupců jth. Například A (3, 2) je položka v matici A 3. řádku a 2. sloupce. Předpokládejme, že jsou matic a AB A, B a C = "c". Položky C jsou vypočítávány následujícím způsobem:  
  
 C (i, j) = (řádek i A) • (sloupec j b)  
  
 Následující obrázek znázorňuje několik příkladů násobení matic.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Pokud si myslíte bodu v rovině jako 1 × 2 matice, můžete tento bod převést vynásobením matice 2 × 2. Následující obrázek znázorňuje několik transformace působí v místě (2, 1).  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Všechny transformace vidět na předchozím obrázku jsou lineární transformace. Některé transformace, jako je například překlad, nejsou lineární a nemůže být vyjádřena jako násobení podle matice 2 × 2. Předpokládejme, že chcete spustit s bodem (2, 1), rotaci o 90 stupňů, přeloží ji 3 jednotky ve směru osy x a přeloží ji 4 jednotky ve směru osy y. Toho lze dosáhnout pomocí násobení matic, za nímž následuje přidání matice.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Lineární transformace (násobení podle matice 2 × 2) a následný překlad (Přidání matice 1 × 2) se nazývá afinní transformace. Alternativou k ukládání afinní transformace v pár matic (jeden pro lineární část) a jeden pro překlad je k uložení celého transformaci v matici 3 x 3. Chcete-li tato práce, musí být bod v rovině uložen v matici 1 × 3 s fiktivní 3. souřadnice. Obvyklým způsobem se provést 3. všechny souřadnice rovna 1. Například bod (2, 1) je reprezentována matice [2 1 1]. Následující obrázek znázorňuje afinní transformace (Otočit 90 stupňů; převede 3 jednotky ve směru osy x, 4 jednotky ve směru osy y) vyjádřený jako násobení podle jednoho 3 x 3 matice.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 V předchozím příkladu bodu (2, 1) je namapována na bod (2, 6). Všimněte si, že třetí sloupec matice 3 x 3 obsahuje čísel od 0, 0, 1. To bude vždy případ matice 3 x 3 afinní transformace. Důležité čísla jsou šest čísel ve sloupci 1 a 2. Levý horní část 2 × 2 matice reprezentuje část lineární transformace, a první dvě položky 3. řádku představují překlad.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 V [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete ukládat afinní transformací v <xref:System.Drawing.Drawing2D.Matrix> objektu. Protože třetí sloupec přehled, který představuje afinní transformace je vždy (0, 0, 1), zadejte pouze šest čísla v první dva sloupce, když vytvoříte <xref:System.Drawing.Drawing2D.Matrix> objektu. Příkaz `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` vytvoří matice vidět na předchozím obrázku.  
  
## <a name="composite-transformations"></a>Kompozitní transformace  
 Složené transformaci je posloupnost transformací, jeden následuje dalších. Vezměte v úvahu matic a transformace v následujícím seznamu:  
  
|||  
|-|-|  
|Matice A|Otočit 90 stupňů.|  
|Matice B|Škálování faktorem 2 ve směru osy x|  
|Matice C|Převede 3 jednotky ve směru osy y|  
  
 Pokud jsme začít s bodem (2, 1) – reprezentována matice [2 1 1] – a vynásobit A, pak B a C, bod (2, 1) se má provést tři transformace v uvedeném pořadí.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Spíše než v tři samostatné matic uložit tyto tři části složené transformace, můžete násobení A, B a C společně získat jeden přehled 3 x 3, který ukládá celý složený transformace. Předpokládejme ABC = D. Poté přiřadí bod násobí hodnotou D stejný výsledek jako bod násobí hodnotou A, pak B, pak C.  
  
 [2 1 1]D = [-2 5 1]  
  
 Následující obrázek znázorňuje matic A, B, C a D.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Fakt, že můžete matice složené transformace tvořeny vynásobením matic jednotlivé transformace znamená, že všechny pořadí afinní transformace může být uložena do jedné <xref:System.Drawing.Drawing2D.Matrix> objektu.  
  
> [!CAUTION]
>  Je důležité pořadí složeného transformace. Obecně platí, otáčení, pak škálování a potom převede není stejný jako měřítko, pak otočit a potom převede. Podobně je důležité pořadí násobení matic. Obecně platí ABC není stejný jako ZÁ.  
  
 <xref:System.Drawing.Drawing2D.Matrix> Třída poskytuje několik metod pro vytváření kompozitních transformace: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, a <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. Následující příklad vytvoří matice složené transformace, která nejprve otočí 30 stupňů, pak škáluje faktorem 2 ve směru osy y a pak překládá 5 jednotky ve směru osy x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Následující obrázek znázorňuje matice.  
  
 ![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Viz také  
 [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Použití transformací ve spravovaném GDI+](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
