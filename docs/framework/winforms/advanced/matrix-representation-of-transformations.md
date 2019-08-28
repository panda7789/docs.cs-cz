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
ms.openlocfilehash: 24da407de24a924a68466e4301cc3f4a74cb2e94
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044242"
---
# <a name="matrix-representation-of-transformations"></a>Maticové znázornění transformací
Matice m × n je množina čísel uspořádaných v m řádcích a n sloupcích. Následující ilustrace znázorňuje několik matic.  
  
 ![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Přidáním jednotlivých prvků můžete přidat dvě matice stejné velikosti. Následující ilustrace znázorňuje dva příklady Sčítání matic.  
  
 ![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Matice m × n se dá vynásobit pomocí matice n × p a výsledkem je matice m × p. Počet sloupců v první matrici musí být stejný jako počet řádků ve druhé matici. Například matice 4 × 2 může být vynásobená maticí 2 × 3, která vytvoří matici 4 × 3.  
  
 Body v rovině a řádky a sloupce matice lze představit jako vektory. Například (2, 5) je vektor se dvěma komponentami a (3, 7, 1) je vektor se třemi komponentami. Koncový součin dvou vektorů je definován následujícím způsobem:  
  
 (a, b) • (c, d) = AC + BD  
  
 (a, b, c) • (d, e, f) = AD + je + CF  
  
 Například produkt s tečkou v (2, 3) a (5, 4) je (2) (5) + (3) (4) = 22. Koncový produkt (2, 5, 1) a (4, 3, 1) je (2) (4) + (5) (3) + (1) (1) = 24. Všimněte si, že tečkové součin dvou vektorů je číslo, nikoli jiný vektor. Všimněte si také, že produkt s tečkou lze vypočítat pouze v případě, že dva vektory mají stejný počet komponent.  
  
 Nechť A (i, j) je položka v matici a v řádku-tého a ve sloupci JTH. Například A (3, 2) je položka v matici a v řádku 3 a v poli druhý sloupec. Předpokládejme, že a, B a C jsou matice a AB = C. Položky jazyka C se vypočtou takto:  
  
 C (i, j) = (řádek i A) • (sloupec j z B)  
  
 Následující ilustrace znázorňuje několik příkladů násobení matic.  
  
 ![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Pokud si myslíte, že je bod v rovině v matici o úrovni 1 × 2, můžete tento bod transformovat tak, že ho vynásobí 2 × 2 matice. Následující ilustrace znázorňuje několik transformací použitých pro bod (2, 1).  
  
 ![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Všechny transformace zobrazené na předchozím obrázku jsou lineární transformace. Některé další transformace, jako je například převod, nejsou lineární a nelze je vyjádřit jako násobení pomocí matice 2 × 2. Předpokládejme, že chcete začít s bodem (2, 1), otočit ho 90 stupňů, přeložit 3 jednotky ve směru x a překládat 4 jednotky ve směru y. Můžete to provést pomocí násobení matice následovaný přidáním matice.  
  
 ![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Lineární transformace (násobení o 2 × 2 matice) následovaná překladem (přídavek 1 × 2 matice) se nazývá transformace spřažení. Alternativa k uložení transformace spřažení do páru matric (jedna pro lineární část a druhá pro překlad) je uložit celou transformaci do matice 3 × 3. Aby bylo možné tuto práci provést, musí být bod v rovině uložen v matrici 1 × 3 s fiktivní třetí souřadnicí. Obvyklou technikou je, aby se všechny 3 souřadnice rovnaly 1. Například bod (2, 1) je reprezentován maticí [2 1 1]. Následující ilustrace znázorňuje transformaci spřažení (otočení 90 stupňů; přeloží 3 jednotky ve směru x, 4 jednotky ve směru y), vyjádřené jako násobení jednou maticí 3 × 3.  
  
 ![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 V předchozím příkladu je bod (2, 1) namapován na bod (2, 6). Všimněte si, že třetí sloupec matice 3 × 3 obsahuje čísla 0, 0, 1. Tato akce bude vždycky v případě matice 3 × 3 transformace spřažení. Důležitá čísla jsou šest čísel ve sloupcích 1 a 2. Levá horní 2 × 2 část matice představuje lineární část transformace a první dvě položky na 3 řádku představují překlad.  
  
 ![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 V rozhraní GDI+ můžete uložit transformaci spřažení do <xref:System.Drawing.Drawing2D.Matrix> objektu. Vzhledem k tomu, že třetí sloupec matice, která představuje transformaci spřažení, je vždy (0, 0, 1), při vytváření <xref:System.Drawing.Drawing2D.Matrix> objektu zadáte pouze šest čísel v prvních dvou sloupcích. Příkaz `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` vytvoří matici zobrazenou na předchozím obrázku.  
  
## <a name="composite-transformations"></a>Složené transformace  
 Složená transformace je posloupnost transformací, jedna následovaná druhým. Vezměte v úvahu matice a transformace v následujícím seznamu:  
  
|||  
|-|-|  
|Matice A|Otočit o 90 stupňů|  
|Matice B|Škálování podle faktoru 2 ve směru x|  
|Matice C|Přeloží 3 jednotky ve směru y.|  
  
 Pokud Začínáme s bodem (2, 1), který je reprezentován maticí [2 1 1], a vynásobí se a, pak B, pak C, bodem (2, 1), bude podléhat třem transformacím v uvedeném pořadí.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Místo uložení tří částí složené transformace ve třech samostatných maticích můžete vynásobit a, B a C dohromady a získat jednu matrici 3 × 3, která ukládá celou složenou transformaci. Předpokládejme, že ABC = D. Pak bod vynásobený D znamená stejný výsledek jako bod vynásobený A, B a pak C.  
  
 [2 1 1]D = [-2 5 1]  
  
 Následující ilustrace znázorňuje matice A, B, C a D.  
  
 ![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 Fakt, že matice složené transformace může být vytvořena vynásobením jednotlivých matic transformace, znamená, že jakákoli sekvence transformací spřažení může být uložena v jednom <xref:System.Drawing.Drawing2D.Matrix> objektu.  
  
> [!CAUTION]
> Pořadí složených transformací je důležité. Obecně platí, že se otočí a pak se nedá přeložit na stejné úrovni jako škálování a pak ho otočit a pak přeložit. Podobně je důležité pořadí Násobení matice. Obecně platí, že ABC není stejné jako BAC.  
  
 <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A> <xref:System.Drawing.Drawing2D.Matrix.Translate%2A> <xref:System.Drawing.Drawing2D.Matrix.Shear%2A> <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A> <xref:System.Drawing.Drawing2D.Matrix.Scale%2A> <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>Třída poskytuje několik metod pro sestavování složené transformace:,,,, a. <xref:System.Drawing.Drawing2D.Matrix> Následující příklad vytvoří matici složené transformace, která nejprve otočí o 30 stupňů, potom se škáluje podle faktoru 2 ve směru y a pak přeloží 5 jednotek ve směru x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 Následující ilustrace znázorňuje matici.  
  
 ![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Viz také:

- [Systém souřadnic a transformace](coordinate-systems-and-transformations.md)
- [Použití transformací ve spravovaném GDI+](using-transformations-in-managed-gdi.md)
