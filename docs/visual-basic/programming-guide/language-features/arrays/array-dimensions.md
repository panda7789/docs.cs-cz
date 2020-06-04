---
title: Rozměry pole
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: f971f0c3693177adbcb8869d487e3ad41d49ddc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413101"
---
# <a name="array-dimensions-in-visual-basic"></a>Rozměry pole v jazyce Visual Basic

*Dimenze* je směr, ve kterém můžete měnit specifikaci prvků pole. Pole, které obsahuje celkový prodej za každý den v měsíci, má jednu dimenzi (den v měsíci). Pole, které obsahuje celkové tržby podle oddělení za každý den v měsíci, má dvě dimenze (číslo oddělení a den v měsíci). Počet rozměrů, které pole je označováno jako *pořadí*.

> [!NOTE]
> Vlastnost můžete použít <xref:System.Array.Rank%2A> k určení, kolik rozměrů pole má.

## <a name="working-with-dimensions"></a>Práce s rozměry

Prvek pole určíte tak, že pro každou z jeho rozměrů zadáte *index* nebo *dolní index* . Prvky jsou souvislé podél každé dimenze z indexu 0 až po nejvyšší index pro tuto dimenzi.

Následující ilustrace znázorňují koncepční strukturu polí s odlišným pořadím. Každý prvek na ilustraci zobrazuje indexové hodnoty, které k němu přistupují. Můžete například získat přístup k prvnímu prvku druhého řádku dvojrozměrného pole zadáním indexů `(1, 0)` .

![Diagram, který zobrazuje jednorozměrné pole.](./media/array-dimensions/one-dimensional-array.gif)

![Diagram, který zobrazuje dvourozměrné pole.](./media/array-dimensions/two-dimensional-array.gif)

![Diagram, který zobrazuje trojrozměrné pole.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a>Jedna dimenze

Mnoho polí má pouze jednu dimenzi, například počet lidí každého stáří. Jediným požadavkem určení prvku je stáří, pro které tento prvek obsahuje počet. Proto takové pole používá pouze jeden index. Následující příklad deklaruje proměnnou tak, aby obsahovala jednorozměrné *pole* počtů stáří pro věkové číslo 0 až 120.

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a>Dvě dimenze

Některá pole mají dvě dimenze, jako je třeba počet poboček na každém patře každé budovy na areálu. Specifikace elementu vyžaduje stavební číslo i podlahu a každý prvek obsahuje počet pro tuto kombinaci sestavování a podlaží. Proto takové pole používá dva indexy. Následující příklad deklaruje proměnnou pro uchování *dvojrozměrného pole* počtů kanceláří pro budovy 0 až 40 a podlah 0 až 5.

```vb
Dim officeCounts(40, 5) As Byte
```

Dvourozměrné pole se označuje také jako *obdélníkové pole*.

### <a name="three-dimensions"></a>Tři rozměry

Několik polí má tři dimenze, například hodnoty v trojrozměrném prostoru. Takové pole používá tři indexy, což v tomto případě představuje souřadnice x, y a z fyzického místa. Následující příklad deklaruje proměnnou pro uchování *trojrozměrného pole* teploty vzduchu v různých místech trojrozměrného svazku.

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a>Více než tři dimenze

I když pole může mít až 32 dimenzí, je zřídka více než tři.

> [!NOTE]
> Když přidáte dimenze do pole, celkové úložiště, které je potřeba pro pole, se výrazně zvětšuje, takže používejte multidimenzionální pole s rozvahou.

## <a name="using-different-dimensions"></a>Používání různých dimenzí

Předpokládejme, že chcete sledovat tržby za každý den v daném měsíci. Je možné deklarovat jednorozměrné pole s 31 prvky, jeden pro každý den v měsíci, jak ukazuje následující příklad.

```vb
Dim salesAmounts(30) As Double
```

Nyní předpokládejme, že chcete sledovat stejné informace nejen pro každý den v měsíci, ale také pro každý měsíc v roce. Můžete deklarovat dvojrozměrné pole s 12 řádky (za měsíc) a 31 sloupců (pro dny), jak ukazuje následující příklad.

```vb
Dim salesAmounts(11, 30) As Double
```

Nyní se můžete rozhodnout, že budete mít informace o poznámkovém poli po dobu více než jednoho roku. Pokud chcete sledovat prodejní objemy po dobu 5 let, můžete deklarovat trojrozměrné pole s 5 vrstvami, 12 řádky a 31 sloupci, jak ukazuje následující příklad.

```vb
Dim salesAmounts(4, 11, 30) As Double
```

Všimněte si, že vzhledem k tomu, že se každý index mění z 0 na jeho maximum, každá dimenze `salesAmounts` je deklarována jako jedna menší než požadovaná délka této dimenze. Všimněte si také, že velikost pole se zvyšuje s každou novou dimenzí. Tři velikosti v předchozích příkladech jsou 31, 372 a 1 860 prvky.

> [!NOTE]
> Pole lze vytvořit bez použití `Dim` příkazu nebo `New` klauzule. Například můžete zavolat <xref:System.Array.CreateInstance%2A> metodu nebo jiná komponenta může předat vašemu kódu pole vytvořené tímto způsobem. Takové pole může mít dolní mez, která je jiná než 0. Můžete vždy testovat spodní mez dimenze pomocí <xref:System.Array.GetLowerBound%2A> metody nebo `LBound` funkce.

## <a name="see-also"></a>Viz také

- [Pole](index.md)
- [Řešení potíží s poli](troubleshooting-arrays.md)
