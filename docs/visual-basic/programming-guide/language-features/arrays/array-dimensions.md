---
title: Rozměry pole v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: cf295288dd034d744dceb71b5c58278be5cc2a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651753"
---
# <a name="array-dimensions-in-visual-basic"></a>Rozměry pole v jazyce Visual Basic
A *dimenze* je směr, ve kterém můžete měnit specifikace elementů tohoto pole. Pole, které obsahuje celkový počet prodeje za každý den v měsíci má jednu dimenzi (den v měsíci). Pole, které obsahuje celkový počet prodeje podle oddělení pro každý den v měsíci se dvěma rozměry (číslo oddělení a den v měsíci). Počet dimenzí pole se nazývá jeho *pořadí*.  
  
> [!NOTE]
>  Můžete použít <xref:System.Array.Rank%2A> vlastnosti k určení, kolik rozměry pole.  
  
## <a name="working-with-dimensions"></a>Práce s dimenzí  
 Zadejte k elementu pole zadáním *index* nebo *dolní index* pro každou z jeho dimenzí. Elementy jsou souvislé každý dimenzi z indexu 0 prostřednictvím nejvyšší index pro daná dimenze.  
  
 Následující ilustrace znázorňuje koncepční strukturu polí se různá pořadí. Každý prvek v tyto ilustrace zobrazuje hodnoty indexu, které k němu přístup. Například můžete první prvek pole dvourozměrná druhý řádek přístup zadáním indexy `(1, 0)`.  
  
 ![Grafický diagram jednoho&#45;dimenzí pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")  
Jednorozměrné pole  
  
 ![Grafický diagram dva&#45;dimenzí pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
Dvourozměrná pole  
  
 ![Grafický diagram tři&#45;dimenzí pole](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
trojrozměrné pole  
  
### <a name="one-dimension"></a>Jednu dimenzi  
 Mnoho pole mají jenom jednou dimenzí, jako je například počet lidí každý věk. Jediným požadavkem k určení element je stáří, pro které daný element obsahuje počet. Proto tyto pole používá jenom jeden index. Následující příklad deklaruje proměnnou pro uložení *jednorozměrné pole* věku počty od 0 do 120.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>Dvě dimenze  
 Některé pole mají dvě dimenze, jako je počet uzlů na každý podlaží každý vytváření ve kanceláře. Specifikace elementu vyžaduje číslo sestavení a podlaží a každý prvek obsahuje počet pro tuto kombinaci budova a podlaží. Proto tyto pole používá dva indexy. Následující příklad deklaruje proměnnou pro uložení *dvourozměrná pole* office součtů pro 0 až 40 budovy a podlaží 0 až 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Je také označován dvourozměrná pole *obdélníková pole*.  
  
### <a name="three-dimensions"></a>Tři dimenze  
 Několik polí mít tři dimenzí, jako je například hodnoty v trojrozměrné prostoru. Takové pole používá tři indexy, které v tomto případě představují x, y a souřadnice z fyzického místa na disku. Následující příklad deklaruje proměnnou pro uložení *trojrozměrné* z teploty letecké v různých fázích trojrozměrné svazku.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Víc než třemi dimenze  
 I když pole může mít maximálně 32 dimenzí, je výjimečná mít víc než tři.  
  
> [!NOTE]
>  Když přidáte dimenze do pole, zvyšuje celkové úložiště vyžaduje pole podstatně, tak vícerozměrná pole použití dát pozor.  
  
## <a name="using-different-dimensions"></a>Pomocí různých dimenzí  
 Předpokládejme, že chcete sledovat částek prodeje pro každý den v měsíci přítomen. Může deklarovat jednorozměrné pole s 31 prvky, jednu pro každý den v měsíci jako následující příklad ukazuje.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Nyní předpokládejme, že chcete sledovat stejné informace, ne jenom pro každý den v měsíci, ale také pro každý měsíc v roce. Může deklarovat dvourozměrná pole s 12 řádků (pro měsíců) a 31 sloupců (pro dny), jak ukazuje následující příklad.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Nyní předpokládejme, že se můžete rozhodnout, že se vaše pole obsahovat informace o více než jeden rok. Pokud chcete sledovat částek prodeje 5 let, může deklarovat trojrozměrné s 5 vrstev, 12 řádků a sloupců 31, jak ukazuje následující příklad.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Všimněte si, že, protože každý index se liší od 0 do jeho maximální každé dimenze `salesAmounts` je deklarován jako jeden menší než má požadovanou délku dané dimenze. Všimněte si také, že velikost pole hodnota se zvyšuje s každou novou dimenzi. Tři velikosti v předchozích ukázkách jsou 31, 372 a 1,860 elementy.  
  
> [!NOTE]
>  Můžete vytvořit pole bez použití `Dim` příkaz nebo `New` klauzule. Například můžete volat <xref:System.Array.CreateInstance%2A> metody nebo jiné komponenty můžete předat kódu matice vytvořené tímto způsobem. Takové pole může mít dolní mez než 0. Můžete se pro dolní hranice dimenze pomocí vždy otestovat <xref:System.Array.GetLowerBound%2A> metoda nebo `LBound` funkce.  
  
## <a name="see-also"></a>Viz také  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
