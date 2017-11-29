---
title: "Vztahy typů v operacích dotazu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b93188475dd2bb00aea044ff178028eb87e00d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Vztahy typů v operacích dotazu (Visual Basic)
Proměnné používané v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotazu operace jsou silného typu a musí být vzájemně kompatibilní. Silného typování se používá ve zdroji dat, v samotném dotazu a při provádění dotazu. Na následujícím obrázku identifikuje termínů používaných k popisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu. Další informace o části dotazu najdete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Dotaz pseudokódu se zvýrazněnými elementy. ] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
Části dotazu LINQ  
  
 Typ proměnné rozsahu v dotazu musí být kompatibilní s typem elementů ve zdroji dat. Typ proměnné dotazu musí být kompatibilní s element pořadí definovaný v `Select` klauzule. Nakonec typ pořadí elementů také musí být kompatibilní s typem řídicí proměnná smyčky, který se používá v `For Each` příkaz, který provede daný dotaz. Tato silného typování usnadňuje identifikace typu chyby při kompilaci.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Díky silného typování pohodlný implementací odvození místního typu, také známé jako *implicitní zadáním*. Funkce používá v předchozím příkladu, a zobrazí se jeho používaných v celém [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a dokumentace. V jazyce Visual Basic odvození místního typu dosahuje jednoduše pomocí `Dim` příkaz bez `As` klauzule. V následujícím příkladu `city` silného jako řetězec.  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  Odvození místního typu funguje pouze tehdy, když `Option Infer` je nastaven na `On`. Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Ale i v případě, že používáte odvození místního typu v dotazu, stejný typ relace nejsou mezi proměnné ve zdroji dat, proměnné dotazu a cyklus zpracování dotazu. Je užitečné při psaní mají základní znalosti o tyto relace typu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy nebo práci s ukázky a příklady kódu v dokumentaci.  
  
 Musíte zadat explicitní typ pro proměnnou rozsahu, která se neshoduje s typem vráceným ze zdroje dat. Můžete určit typ proměnné rozsahu pomocí `As` klauzule. Ale to vede k chybě pokud převod [zužující převod](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a `Option Strict` je nastaven na `On`. Proto doporučujeme provést převod na hodnoty získané z datového zdroje. Hodnoty můžete převést ze zdroje dat na typ proměnné rozsahu explicitní pomocí <xref:System.Linq.Enumerable.Cast%2A> metoda. Můžete také obsadit hodnot vybraných v `Select` klauzule explicitní typ, který je odlišný od typu proměnnou rozsahu. Tyto body jsou znázorněné v následujícím kódu.  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Dotazy, které vracejí celý elementy zdrojových dat.  
 Následující příklad ukazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operace, která vrací posloupnost elementy vybrané ze zdrojových dat dotazů. Zdroje, `names`, obsahuje pole řetězců, a výstupu dotazu je posloupnost obsahující řetězce, které začínají písmeno M.  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 To je ekvivalentní následující kód, ale je mnohem kratší a psát. Závislá na odvození místního typu v dotazech je upřednostňovaný styl v jazyce Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 V obou předchozích ukázky kódu, existují následující relace, zda typy jsou určeny implicitně nebo explicitně.  
  
1.  Typ elementů ve zdroji dat `names`, je typ proměnné rozsahu `name`, v dotazu.  
  
2.  Typ objektu, který je vybraný `name`, určuje typ proměnné dotazu `mNames`. Zde `name` je řetězec, proměnné v dotazu je rozhraní IEnumerable (Of String) v jazyce Visual Basic.  
  
3.  Dotaz definované v `mNames` se spouštějí v tom `For Each` smyčky. Smyčky iteruje nad výsledek provedení dotazu. Protože `mNames`, když je proveden, vrátí pořadí řetězců, proměnné iterace smyčky, `nm`, také obsahuje řetězec.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Dotazy, které vrátí jedno pole z vybrané elementy  
 Následující příklad ukazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operace, která vrací posloupnost obsahující pouze jednu část jednotlivých prvků vybrané ze zdroje dat dotazů. Dotaz vezme kolekci `Customer` objektů jako svůj zdroj dat a projekty pouze `Name` vlastnost ve výsledku. Protože jméno zákazníka je řetězec, vytvoří dotaz posloupnost řetězce jako výstup.  
  
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
  
 Vztahy mezi proměnné jsou stejně jako v příkladu jednodušší.  
  
1.  Typ elementů ve zdroji dat `customers`, je typ proměnné rozsahu `cust`, v dotazu. V tomto příkladu, který je typu `Customer`.  
  
2.  `Select` Příkaz vrátí `Name` vlastnost jednotlivých `Customer` objektu, nikoli celý objekt. Protože `Name` je řetězec dotazu proměnné `custNames`, bude znovu být IEnumerable (Of String), není `Customer`.  
  
3.  Protože `custNames` představuje posloupnost řetězce, `For Each` proměnné iterace smyčky, `custName`, musí být řetězec.  
  
 Bez odvození místního typu bude předchozí příklad těžkopádnější zápisu a pochopit, jak ukazuje následující příklad.  
  
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
 Následující příklad ukazuje složitější situaci. V předchozím příkladu bylo nepraktické explicitně určit typy pro všechny proměnné. V tomto příkladu není možné. Místo výběru celé `Customer` elementy ze zdroje dat nebo jediné pole z jednotlivých prvků `Select` klauzule v tomto dotazu vrátí dvě vlastnosti původního `Customer` objekt: `Name` a `City`. V reakci `Select` klauzuli kompilátor definuje anonymní typ, který obsahuje tyto dvě vlastnosti. Výsledek provedení `nameCityQuery` v `For Each` smyčka je kolekci instancí nového anonymního typu. Protože anonymní typ nemá žádný použitelný název, nemůžete zadat typ `nameCityQuery` nebo `custInfo` explicitně. To znamená, s anonymní typ, máte název typu používat místě `String` v `IEnumerable(Of String)`. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
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
  
 I když není možné určit typy pro všechny proměnné v předchozím příkladu, vztahy zůstávají stejné.  
  
1.  Typ elementů ve zdroji dat je znovu typ proměnné rozsahu v dotazu. V tomto příkladu `cust` je instance `Customer`.  
  
2.  Protože `Select` příkaz vytvoří instanci anonymního typu proměnnou dotazu `nameCityQuery`, musí být zadán implicitně jako anonymní typ. Anonymní typ nemá žádný použitelný název a proto nemůže být explicitně určen.  
  
3.  Typ proměnné iterace ve `For Each` smyčka je anonymní typ vytvořili v kroku 2. Vzhledem k tomu, že typ nemá žádný použitelný název, typ proměnné iterace smyčky musí určit implicitně.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)
