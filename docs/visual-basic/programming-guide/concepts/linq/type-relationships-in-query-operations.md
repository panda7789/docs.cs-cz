---
title: Vztahy typů v operacích dotazu
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
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406726"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Vztahy typů v operacích dotazu (Visual Basic)

Proměnné používané v operacích dotazu LINQ (Language-Integrated Query) jsou silného typu a musí být vzájemně kompatibilní. Silné zadání se používá ve zdroji dat, v samotném dotazu a v provádění dotazu. Následující ilustrace identifikuje výrazy používané k popisu dotazu LINQ. Další informace o částech dotazu najdete v tématu [základní operace dotazů (Visual Basic)](basic-query-operations.md).

![Snímek obrazovky znázorňující dotaz pseudokódu s zvýrazněnými prvky](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Typ proměnné rozsahu v dotazu musí být kompatibilní s typem prvků ve zdroji dat. Typ proměnné dotazu musí být kompatibilní s elementem Sequence definovaným v `Select` klauzuli. Nakonec musí být typ elementů sekvence také kompatibilní s typem řídicí proměnné smyčky, která je použita v `For Each` příkazu, který spouští dotaz. Toto silné zadání usnadňuje identifikaci chyb typu v době kompilace.

Visual Basic usnadňuje silné psaní implementací místního typu, označovaného také jako *implicitní psaní*. Tato funkce se používá v předchozím příkladu a zobrazí se v ní v ukázkách a dokumentaci pro LINQ. V Visual Basic je odvození místního typu provedeno jednoduše pomocí `Dim` příkazu bez `As` klauzule. V následujícím příkladu `city` je silně typované jako řetězec.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> Odvození místního typu funguje pouze v případě `Option Infer` , že je nastavena na `On` . Další informace naleznete v tématu [příkaz Option include](../../../language-reference/statements/option-infer-statement.md).

Nicméně i v případě, že použijete místní odvození typu v dotazu, jsou přítomny stejné vztahy typů mezi proměnné ve zdroji dat, proměnnou dotazu a smyčkou provedení dotazu. Při psaní dotazů LINQ nebo při práci s ukázkami a příklady kódu v dokumentaci je vhodné mít základní znalosti těchto vztahů typů.

Možná budete muset zadat explicitní typ pro proměnnou rozsahu, která se neshoduje s typem vráceným ze zdroje dat. Můžete zadat typ proměnné rozsahu pomocí `As` klauzule. Nicméně výsledkem je chyba, pokud je převod [zužujícího převodu](../../language-features/data-types/widening-and-narrowing-conversions.md) a `Option Strict` je nastaven na `On` . Proto doporučujeme, abyste provedli převod na hodnoty načtené ze zdroje dat. Hodnoty z datového zdroje můžete převést na typ proměnné explicitní rozsah pomocí <xref:System.Linq.Enumerable.Cast%2A> metody. Můžete také přetypovat hodnoty vybrané v `Select` klauzuli na explicitní typ, který se liší od typu proměnné rozsahu. Tyto body jsou znázorněny v následujícím kódu.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Dotazy, které vracejí celé prvky zdrojových dat

Následující příklad ukazuje operaci dotazu LINQ, která vrací sekvenci prvků vybraných ze zdrojových dat. Zdroj, `names` , obsahuje pole řetězců a výstup dotazu je sekvence obsahující řetězce, které začínají písmenem M.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

To je ekvivalentní následujícímu kódu, ale je mnohem kratší a snazší psát. Spoléhání na odvození místního typu v dotazech je preferovaným stylem v Visual Basic.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Následující vztahy existují v obou předchozích příkladech kódu, ať už jsou typy určeny implicitně nebo explicitně.

1. Typ prvků ve zdroji dat, `names` je typ proměnné rozsahu, `name` v dotazu.

2. Typ objektu, který je vybrán, `name` Určuje typ proměnné dotazu `mNames` . Zde `name` je řetězec, takže proměnná dotazu je IEnumerable (Of String) v Visual Basic.

3. Dotaz definovaný v `mNames` je proveden ve `For Each` smyčce. Smyčka prochází výsledek provedení dotazu. Vzhledem k tomu `mNames` , že při spuštění vrátí posloupnost řetězců, proměnná iterace smyčky, `nm` a také řetězec.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Dotazy, které vracejí jedno pole z vybraných elementů

Následující příklad ukazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci dotazu, která vrací sekvenci obsahující pouze jednu část každého prvku vybranou ze zdroje dat. Dotaz převezme kolekci `Customer` objektů jako zdroj dat a projekty zobrazí pouze `Name` vlastnost ve výsledku. Vzhledem k tomu, že název zákazníka je řetězec, dotaz vytvoří sekvenci řetězců jako výstup.

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

1. Typ prvků ve zdroji dat, `customers` je typ proměnné rozsahu, `cust` v dotazu. V tomto příkladu je tento typ `Customer` .

2. `Select`Příkaz vrátí `Name` vlastnost všech `Customer` objektů namísto celého objektu. Vzhledem k tomu, `Name` že je řetězec, proměnná dotazu, `custNames` ,,, bude znovu typu IEnumerable (Of String), nikoli `Customer` .

3. Vzhledem k tomu, že `custNames` představuje sekvenci řetězců, `For Each` iterační proměnná smyčky, `custName` musí být řetězec.

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

Následující příklad ukazuje složitější situaci. V předchozím příkladu bylo nepohodlné určit typy pro všechny proměnné explicitně. V tomto příkladu není možné. Namísto výběru celých `Customer` prvků ze zdroje dat nebo jednoho pole z každého prvku `Select` vrátí klauzule v tomto dotazu dvě vlastnosti původního `Customer` objektu: `Name` a `City` . V reakci na `Select` klauzuli kompilátor definuje anonymní typ, který obsahuje tyto dvě vlastnosti. Výsledek spuštění `nameCityQuery` ve `For Each` smyčce je kolekce instancí nového anonymního typu. Vzhledem k tomu, že anonymní typ nemá žádný použitelný název, nelze zadat `nameCityQuery` ani `custInfo` explicitně typ. To znamená, že u anonymního typu není k dispozici žádný název typu, který by bylo možné použít místo `String` v `IEnumerable(Of String)` . Další informace najdete v tématu [anonymní typy](../../language-features/objects-and-classes/anonymous-types.md).

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

1. Typ prvků ve zdroji dat je znovu typem proměnné rozsahu v dotazu. V tomto příkladu `cust` je instance `Customer` .

2. Vzhledem k tomu, že `Select` příkaz vytvoří anonymní typ, proměnná dotazu, `nameCityQuery` musí být implicitně typu jako anonymní typ. Anonymní typ nemá žádný použitelný název, a proto jej nelze zadat explicitně.

3. Typ iterační proměnné ve `For Each` smyčce je anonymní typ vytvořený v kroku 2. Vzhledem k tomu, že typ nemá žádný použitelný název, je nutné určit typ proměnné iterace smyčky implicitně.

## <a name="see-also"></a>Viz také

- [Začínáme s dotazy LINQ v jazyce Visual Basic](getting-started-with-linq.md)
- [Anonymní typy](../../language-features/objects-and-classes/anonymous-types.md)
- [Odvození místního typu](../../language-features/variables/local-type-inference.md)
- [Představení technologie LINQ v jazyce Visual Basic](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Dotazy](../../../language-reference/queries/index.md)
