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
ms.openlocfilehash: 14f17e89e2a4143580b4a2ca7f9d30013ded58f9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327630"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Vztahy typů v operacích dotazu (Visual Basic)
Proměnné použité v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotazu operace jsou silného typu a musí být navzájem kompatibilní. Silné typování se používá ve zdroji dat, v samotném dotazu a ve spuštění dotazu. Následující obrázek označuje termíny používané k popisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu. Další informace o části dotazu, naleznete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Snímek obrazovky zobrazující pseudokódu dotazu se zvýrazněnými elementy.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 Musí být kompatibilní s typem prvků ve zdroji dat typu proměnné rozsahu v dotazu. Typ proměnné dotazu musí být kompatibilní s pořadí element definovaný v `Select` klauzuli. Nakonec typu pořadí elementů také musí být kompatibilní s typem řídicí proměnná smyčky for, který se používá v `For Each` příkaz, který provede daný dotaz. Silné typování usnadňuje identifikaci chyby typu v době kompilace.  
  
 Visual Basic umožňuje silného typování pohodlný implementací odvození místního typu, označované také jako *implicitního zápisu*. Že v předchozím příkladu se používá funkce, a zobrazí se používá v rámci [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a dokumentaci. V jazyce Visual Basic, se jednoduše tak, že pomocí provádí odvození místního typu `Dim` příkaz bez `As` klauzuli. V následujícím příkladu `city` je silně typováno jako řetězec.  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Odvození místního typu funguje pouze tehdy, když `Option Infer` je nastavena na `On`. Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Ale i v případě použití odvození místního typu v dotazu, stejný typ relace jsou k dispozici mezi proměnné ve zdroji dat, proměnná dotazu a smyčka provádění dotazu. Je užitečné mít základní znalosti o těchto vztahů typů, když vytváříte [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy nebo práce s ukázky a příklady kódu v dokumentaci.  
  
 Budete muset zadat explicitní typ pro proměnnou rozsahu, který typ vrácený ze zdroje dat se neshoduje. Druh proměnné rozsahu můžete zadat pomocí `As` klauzuli. Nicméně to způsobí chybu při převodu [zužující převod](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a `Option Strict` je nastavena na `On`. Proto doporučujeme provést převod na hodnoty získané ze zdroje dat. Hodnoty lze převést ze zdroje dat na typ proměnné explicitního rozsahu pomocí <xref:System.Linq.Enumerable.Cast%2A> metody. Můžete také přetypování hodnoty vybrané v `Select` klauzule explicitního typu, který se liší od typu proměnné rozsahu. Tyto body jsou znázorněné v následujícím kódu.  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Dotazy vracející celé prvky zdroje dat  
 Následující příklad ukazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operaci, která vrátí sekvenci prvků vybrané ze zdroje dat dotazu. Zdroj, `names`, obsahuje pole řetězců a výstup dotazu je sekvence obsahující řetězce, které začínají písmenem M.  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 To je ekvivalentní následujícímu kódu, ale je mnohem kratší a jednodušší pro zápis. Závislost na odvození místního typu v dotazech je upřednostňovaný stylu v jazyce Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 V obou předchozí příklady kódu, existují následující relace, zda typy jsou určeny implicitně nebo explicitně.  
  
1. Typ prvků ve zdroji dat `names`, je druh proměnné rozsahu `name`, v dotazu.  
  
2. Typ objektu, který je vybrán, `name`, určuje typ proměnné dotazu `mNames`. Tady `name` je řetězec, proměnná dotazu je IEnumerable (Of String) v jazyce Visual Basic.  
  
3. Dotaz definovaný v `mNames` se provádí `For Each` smyčky. Smyčky Iteruje přes výsledek provedení dotazu. Protože `mNames`, pokud je spuštěn, vrátí sekvencí řetězců, iterační proměnná smyčky `nm`, je také řetězec.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Dotazy, které vracejí jedno pole z vybraných elementů  
 Následující příklad ukazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci, která vrátí sekvenci, který obsahuje pouze jednu část každý prvek vybrané ze zdroje dat dotazu. Dotaz vezme kolekci `Customer` objektů jako svůj zdroj dat a pouze pro projekty `Name` vlastnosti ve výsledku. Protože název zákazníka je řetězec, dotaz vyprodukuje sekvenci řetězců jako výstup.  
  
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
  
 Vztahy mezi proměnné jsou podobné těm v příkladu jednodušší.  
  
1. Typ prvků ve zdroji dat `customers`, je druh proměnné rozsahu `cust`, v dotazu. V tomto příkladu, který je typu `Customer`.  
  
2. `Select` Příkaz vrátí `Name` vlastnosti každého `Customer` objektu, nikoli celý objekt. Protože `Name` řetězce, proměnná dotazu je `custNames`, bude znovu nebyl IEnumerable (Of String) o `Customer`.  
  
3. Protože `custNames` představuje posloupnost řetězců, `For Each` iterační proměnná smyčky `custName`, musí být řetězec.  
  
 Bez odvození místního typu v předchozím příkladu by těžkopádnější k zápisu a informace o tom, jak ukazuje následující příklad.  
  
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
 Následující příklad ukazuje mnohem složitější situace. V předchozím příkladu bylo nepraktické explicitně určit typy všech proměnných. V tomto příkladu je nemožné. Místo výběru celé `Customer` elementy ze zdroje dat, nebo jedno pole z každého prvku `Select` klauzule v tomto dotazu vrátí dvě vlastnosti původní `Customer` objektu: `Name` a `City`. V reakci `Select` klauzule, kompilátor definuje anonymního typu, který obsahuje tyto dvě vlastnosti. Výsledek provedení `nameCityQuery` v `For Each` smyčky je kolekci instancí novém anonymním typu. Protože anonymního typu nemá žádný použitelný název, nelze zadat typ `nameCityQuery` nebo `custInfo` explicitně. To znamená, pomocí anonymního typu, máte název bez typu použít místo `String` v `IEnumerable(Of String)`. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
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
  
 Ačkoli to není možné určit typy pro všechny proměnné v předchozím příkladu, vztahy zůstávají stejné.  
  
1. Typ prvků ve zdroji dat je znovu typu proměnné rozsahu v dotazu. V tomto příkladu `cust` je instance `Customer`.  
  
2. Protože `Select` příkaz produkuje anonymní typ, proměnná dotazu `nameCityQuery`, musí být implicitně typované jako anonymního typu. Anonymní typ nemá žádný použitelný název a proto nelze zadat explicitně.  
  
3. Typ proměnné iterace ve `For Each` smyčky je anonymní typ vytvořili v kroku 2. Vzhledem k tomu, že typ nemá žádný použitelný název, třeba implicitně určit typ proměnné iterace smyčky.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Představení technologie LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
