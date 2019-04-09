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
ms.openlocfilehash: c87be8eaf715e373da75dd8f91889b0e396dba0d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172780"
---
# <a name="matrix-representation-of-transformations"></a>Maticové znázornění transformací
Matici m x n je sadu čísel, které jsou uspořádány do milionů řádků a sloupců n. Následující obrázek znázorňuje několik matice.  
  
 ![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Přidáním jednotlivým prvkům můžete přidat dvěma matice stejné velikosti. Následující obrázek ukazuje dva příklady přidávání matice.  
  
 ![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Matici m x n můžete vynásobí matici p x n a výsledkem je matici m x p. Počet sloupců v první matice musí být stejný jako počet řádků v druhé matice. Například můžete matice 4 x 2 vynásobené 2 × 3 matice pro vytvoření matice 4 x 3.  
  
 Body v rovině a řádky a sloupce matice můžete představit jako vektorů. Například (2, 5) je vektor s dvě komponenty a (3, 7, 1) je vektor tří součástí. Součin dvou vektorů je definovaná následujícím způsobem:  
  
 (a, b) • (c, d) = ac + bd  
  
 (a, b, c) • (d, e, f) = ad + být + cf  
  
 Například součin z (2, 3) a (5, 4) je (2)(5) + (3)(4) = 22. SOUČIN (2, 5, 1) a (4, 3, 1) je (2)(4) + (5)(3) + (1)(1) = 24. Všimněte si, že součin dvou vektorů je číslo, ne jiným způsobem. Všimněte si také, že můžete vypočítat součin pouze v případě, že dva vektory mít stejný počet prvků.  
  
 Umožní A(i, j) být položka v matici A nejnovějšími řádku a sloupci jth. Například A (3, 2) je položka v matici A v řádku 3. a 2 sloupce. Předpokládejme, že jsou A, B a C matice a AB = C. Položky jazyka C jsou vypočítávány následujícím způsobem:  
  
 C (i, j) = (řádek i A) • (sloupec j B)  
  
 Následující obrázek znázorňuje několik příkladů násobení matic.  
  
 ![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Pokud si představíte bod v rovině jako 1 × 2 matice, můžete transformovat tento bod vynásobením matice 2 x 2. Následující obrázek znázorňuje několik transformace použít pro bod (2, 1).  
  
 ![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Všechny transformace je vidět na předchozím obrázku jsou lineární transformace. Některé transformace, jako je například překladu, nejsou lineární a nelze vyjádřen jako násobení hodnotou 2 × 2 matice. Předpokládejme, že chcete začít s bod (2, 1), otočit o 90 stupňů, přeložit 3 jednotky ve směru osy x a přeloží ji 4 jednotky ve směru osy y. Můžete to provést pomocí násobení matic, za nímž následuje záležitostí matice.  
  
 ![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Lineární transformace (násobení podle matice 2 × 2), za nímž následuje překlad (součet matice 1 × 2) se nazývá afinní transformace. Alternativa k ukládání afinní transformace páru matice (jeden pro lineární část) a jeden pro překlad je pro uložení celé transformace v matici 3 × 3. Chcete-li tuto práci, bod v rovině musí být uložen v matici 1 × 3 fiktivní 3. souřadnice. Běžné techniky je, aby všechny 3. souřadnice rovnající se 1. Například bod (2, 1) je představován matice [2 1 1]. Následující obrázek znázorňuje afinní transformace (Otočit o 90 stupňů; přeložit 3 jednotky ve směru osy x, 4 jednotky ve směru osy y) vyjádřený jako násobení pomocí jednoho 3 × 3 matice.  
  
 ![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 V předchozím příkladu bod, (2, 1) je namapována na bod (2, 6). Všimněte si, že třetí sloupec 3 × 3 matice obsahuje čísla od 0, 0, 1. To bude vždy případ 3 × 3 matice afinní transformace. Šest čísla ve sloupci 1 a 2 jsou důležitá čísla. Část 2 × 2 levého horního rohu maticového představuje lineární součástí transformace a první dvě položky na řádku 3. představují překlad.  
  
 ![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 V [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] afinní transformace v může ukládat <xref:System.Drawing.Drawing2D.Matrix> objektu. Třetí sloupec matrice, který představuje afinní transformace je vždy (0, 0, 1), zadejte pouze šest čísla v prvních dvou sloupcích při vytváření <xref:System.Drawing.Drawing2D.Matrix> objektu. Příkaz `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` vytvoří matice je vidět na předchozím obrázku.  
  
## <a name="composite-transformations"></a>Kompozitní transformace  
 Kompozitní transformace je sekvence transformací, jeden za nímž následuje druhé. Vezměte v úvahu matice a transformace v následujícím seznamu:  
  
|||  
|-|-|  
|Matice|Otočit o 90 stupňů|  
|Matrix B|Škálování faktorem 2 ve směru osy x|  
|Matrix C|Přeložit 3 jednotky ve směru osy y|  
  
 Pokud Začneme s bodem (2, 1), reprezentovaný matice [2 1 1] – a vynásobit, pak B a C, bod, (2, 1) projdou tři transformace v uvedeném pořadí.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Spíše než tři části kompozitní transformace uložit do tří samostatných matice, můžete násobení A, B a C společně se získat jednu matice 3 × 3, který ukládá celý kompozitní transformace. Předpokládejme, že ABC = D. Poté přiřadí bod vynásobené D stejný výsledek jako bod vynásobené A, pak B, pak C.  
  
 [2 1 1]D = [-2 5 1]  
  
 Následující obrázek znázorňuje matice A, B, C a D.  
  
 ![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Fakt, že můžete být tvořen matice kompozitní transformace pro násobení matic jednotlivých transformace znamená, že libovolnou posloupností afinní transformace, můžou být uložené v jediné <xref:System.Drawing.Drawing2D.Matrix> objektu.  
  
> [!CAUTION]
>  Je důležité pořadí kompozitní transformace. Obecně platí, otáčet, škálování, pak přeložit není stejný jako měřítko, pak otočit a pak přeložit. Podobně je důležité pořadí násobení matic. Obecně platí ABC není stejný jako ZÁ.  
  
 <xref:System.Drawing.Drawing2D.Matrix> Třída poskytuje několik metod pro vytváření složených transformace: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, a <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. Následující příklad vytvoří matice kompozitní transformace, která nejprve otočí 30 stupňů, pak škáluje faktorem 2 ve směru osy y a potom převede 5 jednotek ve směru osy x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Následující obrázek znázorňuje matice.  
  
 ![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Viz také:

- [Systém souřadnic a transformace](coordinate-systems-and-transformations.md)
- [Použití transformací ve spravovaném GDI+](using-transformations-in-managed-gdi.md)
