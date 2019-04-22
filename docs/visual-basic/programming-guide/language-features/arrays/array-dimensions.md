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
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836932"
---
# <a name="array-dimensions-in-visual-basic"></a>Rozměry pole v jazyce Visual Basic
A *dimenze* je směr, ve kterém můžete měnit specifikace prvků tohoto pole. Pole, která obsahuje celkový prodej za každý den v měsíci má jednu dimenzi (den v měsíci). Pole, která obsahuje celkový prodej podle oddělení pro každý den v měsíci má dvě dimenze (číslo oddělení a den v měsíci). Počet rozměrů pole má nazývá jeho *pořadí*.  
  
> [!NOTE]
>  Můžete použít <xref:System.Array.Rank%2A> vlastnosti k určení, kolik rozměry pole.  
  
## <a name="working-with-dimensions"></a>Práce s rozměry  
 Určit element pole zadáním *index* nebo *dolní index* pro každé své dimenze. Prvky jsou souvislé podél každé dimenze od indexu 0 až po nejvyšší index pro tuto dimenzi.  
  
 Na následujících obrázcích je koncepční struktura polí se různé rozměry. Každý prvek na obrázcích zobrazuje hodnoty indexu, které k němu přístup. Například můžete přístup k první prvek druhého řádku dvourozměrné pole tak, že zadáte indexy `(1, 0)`.  
  
 ![Diagram zobrazující průběh jednorozměrné pole.](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![Diagram zobrazující průběh dvourozměrné pole.](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![Diagram zobrazující průběh trojrozměrného pole.](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a>Jedna dimenze  
 Mnoho pole mají pouze jednu dimenzi, například počet lidí každý věk. Chcete-li určit element Jediným požadavkem je věk, pro které tento prvek obsahuje počet. Proto se takové pole používá pouze jeden index. Následující příklad deklaruje proměnnou pro uchování *jednorozměrné pole* věku se počítá od 0 až 120.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>Dvě dimenze  
 Některá pole mají dvě dimenze, jako je počet uzlů na každý floor každou vytváření aplikací na areálu. Specifikace prvek vyžaduje číslo sestavení a dolní mez, a každý prvek obsahuje počet pro kombinaci budova a podlaží. Proto se takové pole používá dva indexy. Následující příklad deklaruje proměnnou pro uchování *dvourozměrné pole* počtu office pro 0 až 40 budovy a podlaží 0 až 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Dvourozměrné pole se také nazývá *pravoúhlého pole*.  
  
### <a name="three-dimensions"></a>Tři dimenze  
 Několik pole mají tři dimenze, jako jsou hodnoty v trojrozměrném prostoru. Tato pole používá tři indexy, které v tomto případě představují x, y a souřadnice z fyzického místa na disku. Následující příklad deklaruje proměnnou pro uchování *trojrozměrného pole* air teploty v různých fázích trojrozměrného svazku.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Více než tři dimenze  
 I když objekt array může mít až 32 rozměrů, zřídka dochází k mají více než tři.  
  
> [!NOTE]
>  Při přidání rozměry pole zvyšuje tak použití vícerozměrná pole s opatrností výrazně, celková velikost úložiště vyžadované pole.  
  
## <a name="using-different-dimensions"></a>Použití různých dimenzí  
 Předpokládejme, že chcete sledovat objem prodeje za každý den tohoto měsíce. Může prohlásit jednorozměrné pole s prvky 31, jeden pro každý den v měsíci jako následující příklad ukazuje.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Nyní předpokládejme, že chcete sledovat stejné informace, nejen pro každý den v měsíci, ale také pro každý měsíc v roce. Může prohlásit dvojrozměrné pole s 12 řádky (měsíců) a 31 sloupce (dny), jak ukazuje následující příklad.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Nyní předpokládejme, že se můžete rozhodnout, že se vaše pole obsahovat informace o více než jeden rok. Pokud chcete sledovat objem prodeje po dobu 5 let, můžete deklarovat trojrozměrného pole s 5 vrstvy, 12 řádků a sloupců do 31, jak ukazuje následující příklad.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Všimněte si, že vzhledem k tomu, že každý index se liší od 0 na maximum, každé dimenze `salesAmounts` je deklarován jako jedna nižší než má požadovanou délku pro tuto dimenzi. Všimněte si také, že velikost pole hodnota se zvyšuje s každou novou dimenzi. Tři velikosti v předchozích příkladech jsou 31, 372 a 1,860 elementy.  
  
> [!NOTE]
>  Můžete vytvořit pole bez použití `Dim` příkazu nebo `New` klauzuli. Například můžete volat <xref:System.Array.CreateInstance%2A> metody nebo jiné součásti předat kód pole vytvořené tímto způsobem. Takový objekt array může mít dolní hranicí jinou než 0. Můžete vždy otestovat pro dolní mez dimenze pomocí <xref:System.Array.GetLowerBound%2A> metoda nebo `LBound` funkce.  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Řešení potíží s poli](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
