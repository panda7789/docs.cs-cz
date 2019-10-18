---
title: Vztahy typů v operacích dotazu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 6d5d13064cceba10d27901ee95aa8b6731620dbb
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524109"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Vztahy typů v operacích dotazu (Visual Basic)

Proměnné používané v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] operacích dotazů jsou silného typu a musí být vzájemně kompatibilní. Silné zadání se používá ve zdroji dat, v samotném dotazu a v provádění dotazu. Následující ilustrace identifikuje výrazy používané k popisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ho dotazu. Další informace o částech dotazu najdete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).

![Snímek obrazovky znázorňující dotaz pseudokódu s zvýrazněnými prvky](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Typ proměnné rozsahu v dotazu musí být kompatibilní s typem prvků ve zdroji dat. Typ proměnné dotazu musí být kompatibilní s elementem Sequence definovaným v klauzuli `Select`. Nakonec musí být typ elementů sekvence také kompatibilní s typem řídicí proměnné smyčky, která je použita v příkazu `For Each`, který spouští dotaz. Toto silné zadání usnadňuje identifikaci chyb typu v době kompilace.

Visual Basic usnadňuje silné psaní implementací místního typu, označovaného také jako *implicitní psaní*. Tato funkce se používá v předchozím příkladu a zobrazí se v ní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a dokumentace. V Visual Basic je odvození místního typu provedeno jednoduše pomocí příkazu `Dim` bez klauzule `As`. V následujícím příkladu je `city` silně typované jako řetězec.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> Odvození místního typu funguje pouze v případě, že je `Option Infer` nastaveno na `On`. Další informace naleznete v tématu [příkaz Option include](../../../../visual-basic/language-reference/statements/option-infer-statement.md).

Nicméně i v případě, že použijete místní odvození typu v dotazu, jsou přítomny stejné vztahy typů mezi proměnné ve zdroji dat, proměnnou dotazu a smyčkou provedení dotazu. Při psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů nebo při práci s ukázkami a příklady kódu v dokumentaci je vhodné mít základní znalosti těchto vztahů s těmito typy.

Možná budete muset zadat explicitní typ pro proměnnou rozsahu, která se neshoduje s typem vráceným ze zdroje dat. Typ proměnné rozsahu lze zadat pomocí klauzule `As`. Výsledkem je ale chyba, pokud je převod [zužujícího převodu](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a `Option Strict` je nastavené na `On`. Proto doporučujeme, abyste provedli převod na hodnoty načtené ze zdroje dat. Hodnoty z datového zdroje můžete převést na typ proměnné explicitní rozsah pomocí metody <xref:System.Linq.Enumerable.Cast%2A>. Hodnoty vybrané v klauzuli `Select` lze také přetypovat na explicitní typ, který se liší od typu proměnné rozsahu. Tyto body jsou znázorněny v následujícím kódu.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Dotazy, které vracejí celé prvky zdrojových dat

Následující příklad ukazuje operaci [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, která vrací sekvenci prvků vybraných ze zdrojových dat. Zdroj, `names` obsahuje pole řetězců a výstup dotazu je sekvence obsahující řetězce, které začínají písmenem M.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

To je ekvivalentní následujícímu kódu, ale je mnohem kratší a snazší psát. Spoléhání na odvození místního typu v dotazech je preferovaným stylem v Visual Basic.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Následující vztahy existují v obou předchozích příkladech kódu, ať už jsou typy určeny implicitně nebo explicitně.

1. Typ prvků ve zdroji dat, `names`, je typ proměnné rozsahu `name` v dotazu.

2. Typ objektu, který je vybrán, `name`, určuje typ proměnné dotazu `mNames`. Zde `name` je řetězec, takže proměnná dotazu je IEnumerable (Of String) v Visual Basic.

3. Dotaz definovaný v `mNames` je proveden ve `For Each` smyčce. Smyčka prochází výsledek provedení dotazu. Vzhledem k tomu, že při spuštění `mNames` dojde k vrácení posloupnosti řetězců, proměnná iterace smyčky, `nm`, je také řetězec.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Dotazy, které vracejí jedno pole z vybraných elementů

Následující příklad ukazuje operaci [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotazu, která vrací sekvenci obsahující pouze jednu část každého prvku vybranou ze zdroje dat. Dotaz převezme kolekci objektů `Customer` jako zdroj dat a projekty ve výsledku vytvoří pouze vlastnost `Name`. Vzhledem k tomu, že název zákazníka je řetězec, dotaz vytvoří sekvenci řetězců jako výstup.

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

Vztahy mezi proměnnými jsou podobně jako v jednodušším příkladu.

1. Typ prvků ve zdroji dat, `customers`, je typ proměnné rozsahu `cust` v dotazu. V tomto příkladu je tento typ `Customer`.

2. Příkaz `Select` vrátí vlastnost `Name` každého objektu `Customer` namísto celého objektu. Vzhledem k tomu, že `Name` je řetězec, proměnná dotazu `custNames`, bude znovu typu IEnumerable (Of String), nikoli `Customer`.

3. Vzhledem k tomu, že `custNames` představuje sekvenci řetězců, iterační proměnná `For Each` smyčky, `custName`, musí být řetězec.

Bez odvození místního typu by byl předchozí příklad nenáročný na zápis a pochopení, jak ukazuje následující příklad.

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a>Dotazy, které vyžadují anonymní typy

Následující příklad ukazuje složitější situaci. V předchozím příkladu bylo nepohodlné určit typy pro všechny proměnné explicitně. V tomto příkladu není možné. Místo výběru celých prvků `Customer` ze zdroje dat nebo jednoho pole z každého prvku vrátí klauzule `Select` v tomto dotazu dvě vlastnosti původního objektu `Customer`: `Name` a `City`. V reakci na klauzuli `Select` definuje kompilátor anonymní typ, který obsahuje tyto dvě vlastnosti. Výsledek spuštění `nameCityQuery` ve smyčce `For Each` je kolekce instancí nového anonymního typu. Vzhledem k tomu, že anonymní typ nemá žádný použitelný název, nelze zadat typ `nameCityQuery` ani `custInfo` explicitně. To znamená, že u anonymního typu není název typu, který by se měl použít místo `String` v `IEnumerable(Of String)`. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

I když není možné určit typy pro všechny proměnné v předchozím příkladu, relace zůstanou stejné.

1. Typ prvků ve zdroji dat je znovu typem proměnné rozsahu v dotazu. V tomto příkladu je `cust` instancí `Customer`.

2. Vzhledem k tomu, že příkaz `Select` vytváří anonymní typ, musí být proměnná dotazu `nameCityQuery`, implicitně zadána jako anonymní typ. Anonymní typ nemá žádný použitelný název, a proto jej nelze zadat explicitně.

3. Typ iterační proměnné ve smyčce `For Each` je anonymní typ vytvořený v kroku 2. Vzhledem k tomu, že typ nemá žádný použitelný název, je nutné určit typ proměnné iterace smyčky implicitně.

## <a name="see-also"></a>Viz také:

- [Začínáme pomocí LINQ v Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
