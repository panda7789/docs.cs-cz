---
title: Základní operace dotazů
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266375"
---
# <a name="basic-query-operations-visual-basic"></a>Základní operace dotazů (Visual Basic)
Toto téma obsahuje stručný úvod do jazykintegrované ho dotazu (LINQ) výrazy v jazyce Visual Basic a některé typické druhy operací, které provádíte v dotazu. Další informace najdete v následujících tématech:  
  
 [Představení technologie LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Dotazy](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Návod: Zápis dotazů ve Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Určení zdroje dat (From)  
 V dotazu LINQ je prvním krokem určení zdroje dat, na který chcete dotazovat. Proto klauzule `From` v dotazu vždy na prvním místě. Operátory dotazů vyberou a vytupují výsledek na základě typu zdroje.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 Klauzule `From` určuje zdroj `customers`dat a *proměnnou rozsahu*. `cust` Proměnná rozsahu je jako proměnná iterace smyčky, s tím rozdílem, že ve výrazu dotazu nedojde k žádné skutečné iteraci. Při spuštění dotazu, často pomocí `For Each` smyčky, proměnná rozsahu slouží jako odkaz `customers`na každý následující prvek v . Vzhledem k tomu, že `cust`kompilátor můžete odvodit typ , není nutné zadat explicitně. Příklady dotazů napsaných s explicitním psaním a bez něj naleznete [v tématu Type Relationships in Query Operations (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)  
  
 Další informace o použití `From` klauzule v jazyce Visual Basic naleznete v tématu [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrování dat (Where)  
 Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logického výrazu. Dotaz pak vrátí pouze ty prvky, pro které je výraz true. Klauzule `Where` se používá k provedení filtrování. Filtr určuje, které prvky ve zdroji dat mají být zahrnuty do výsledné sekvence. V následujícím příkladu jsou zahrnuty pouze zákazníci, kteří mají adresu v Londýně.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Můžete použít logické operátory, jako `And` jsou a `Where` `Or` kombinovat výrazy filtru v klauzuli. Chcete-li například vrátit pouze zákazníky, kteří jsou z Londýna a jejichž jméno je Devon, použijte následující kód:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 Chcete-li vrátit zákazníkům z Londýna nebo Paříže, použijte následující kód:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Další informace o použití `Where` klauzule v jazyce Visual Basic naleznete v tématu [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Řazení dat (Order By)  
 Často je vhodné seřadit vrácená data do určitého pořadí. Klauzule `Order By` způsobí, že prvky ve vrácené sekvenci budou seřazeny podle zadaného pole nebo polí. Například následující dotaz seřadí výsledky `Name` na základě vlastnosti. Protože `Name` je řetězec, vrácená data budou seřazena abecedně, od A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Chcete-li výsledky seřadit v opačném pořadí `Order By...Descending` od Z do A, použijte klauzuli. Výchozí hodnota `Ascending` je, `Ascending` `Descending` když ani není zadán.  
  
 Další informace o použití `Order By` klauzule v jazyce Visual Basic naleznete v [tématu Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Výběr dat (Select)  
 Klauzule `Select` určuje formu a obsah vrácených prvků. Můžete například určit, zda se výsledky `Customer` budou skládat z úplných objektů, pouze z jedné `Customer` vlastnosti, podmnožiny vlastností, kombinace vlastností z různých zdrojů dat nebo z nějakého nového typu výsledku založeného na výpočtu. Když `Select` klauzule vytvoří něco jiného než kopii zdrojového prvku, operace se nazývá *projekce*.  
  
 Chcete-li načíst kolekci, která se skládá z úplných `Customer` objektů, vyberte samotnou proměnnou rozsahu:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Pokud `Customer` je instance velký objekt, který má mnoho polí a vše, co `cust.Name`chcete načíst, je název, můžete vybrat , jak je znázorněno v následujícím příkladu. Odvození místního typu rozpozná, že to změní `Customer` typ výsledku z kolekce objektů na kolekci řetězců.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Chcete-li vybrat více polí ze zdroje dat, máte dvě možnosti:  
  
- V `Select` klauzuli zadejte pole, která chcete zahrnout do výsledku. Kompilátor definuje anonymní typ, který má tato pole jako jeho vlastnosti. Další informace naleznete [v tématu Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Vzhledem k tomu, že vrácené prvky v následujícím příkladu jsou instance anonymního typu, nelze odkazovat na typ podle názvu jinde v kódu. Název typu určený kompilátorem obsahuje znaky, které nejsou platné v normálním kódu jazyka Visual Basic. V následujícím příkladu jsou prvky v kolekci, `londonCusts4` které jsou vráceny dotazem v instancí anonymního typu  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -nebo-  
  
- Definujte pojmenovaný typ, který obsahuje konkrétní pole, která chcete zahrnout do výsledku, a `Select` vytvořte a inicializujte instance typu v klauzuli. Tuto možnost použijte pouze v případě, že máte použít jednotlivé výsledky mimo kolekci, ve které jsou vráceny, nebo pokud je musíte předat jako parametry ve volání metod. Typ `londonCusts5` v následujícím příkladu je IEnumerable(Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Další informace o použití `Select` klauzule v jazyce Visual Basic naleznete v [tématu Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Spojování dat (Join a Group Join)  
 V klauzuli `From` můžete zkombinovat více než jeden zdroj dat několika způsoby. Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku. Dotaz vybere studenty, jejichž příjmení začíná samohláská.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Tento kód můžete spustit se seznamem studentů vytvořeným v [části Postup: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Klíčové `Join` slovo je `INNER JOIN` ekvivalentní v SQL. Kombinuje dvě kolekce založené na odpovídající hodnoty klíče mezi prvky v obou kolekcích. Dotaz vrátí všechny nebo část kolekce prvků, které mají odpovídající hodnoty klíče. Například následující kód duplikuje akci předchozího implicitního spojení.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`kombinuje kolekce do jedné hierarchické kolekce, `LEFT JOIN` stejně jako v SQL. Další informace naleznete v [tématu Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) a [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Seskupování dat (Group By)  
 Můžete přidat `Group By` klauzuli seskupit prvky ve výsledku dotazu podle jednoho nebo více polí prvků. Například následující kód seskupuje studenty podle roku třídy.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Pokud spustíte tento kód pomocí seznamu studentů vytvořených v [části Postup: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), výstup z příkazu `For Each` je:  
  
 Rok: Junior  
  
 Tucker, Michael  
  
 Garciová, Hugo  
  
 Garciová, Debra  
  
 Tucker, Kopí  
  
 Rok: Senior  
  
 Omelčenko, Světlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Rok: Prvák  
  
 Mortensen, Sven  
  
 Garciová, Cesar  
  
 Odchylka uvedená v následujícím kódu objednává ročníky a poté objednává studenty v rámci každého roku podle příjmení.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Další informace `Group By`naleznete v [tématu Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic.IEnumerable%601>
- [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [Standardní operátory dotazů – přehled (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
