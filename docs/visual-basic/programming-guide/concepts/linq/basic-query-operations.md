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
ms.openlocfilehash: 92ac5beb70526795eb140bd794e47981cebfea93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410913"
---
# <a name="basic-query-operations-visual-basic"></a>Základní operace dotazů (Visual Basic)
Toto téma poskytuje stručný úvod do výrazů LINQ (Language-Integrated Query) v Visual Basic a na některé běžné druhy operací, které v dotazu provedete. Další informace najdete v následujících tématech:  
  
 [Představení technologie LINQ v jazyce Visual Basic](../../language-features/linq/introduction-to-linq.md)  
  
 [Dotazy](../../../language-reference/queries/index.md)  
  
 [Návod: Zápis dotazů ve Visual Basic](walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Určení zdroje dat (From)  
 V dotazu LINQ je prvním krokem určení zdroje dat, který chcete dotazovat. Proto je `From` klauzule v dotazu vždy první. Operátory dotazu vyberou a tvarují výsledek na základě typu zdroje.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From`Klauzule určuje zdroj dat, `customers` a *proměnnou rozsahu* `cust` . Proměnná rozsahu je jako proměnná iterace smyčky, s výjimkou toho, že ve výrazu dotazu není k dispozici žádná skutečná iterace. Když je dotaz proveden, často pomocí `For Each` smyčky, proměnná rozsahu slouží jako odkaz na každý následný prvek v `customers` . Vzhledem k tomu, že kompilátor může odvodit typ `cust` , nemusíte ho explicitně určovat. Příklady dotazů napsaných pomocí a bez explicitního zadávání najdete v tématu [vztahy typů v operacích dotazu (Visual Basic)](type-relationships-in-query-operations.md).  
  
 Další informace o použití `From` klauzule v Visual Basic naleznete v části [from klauzule](../../../language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrování dat (Where)  
 Pravděpodobně nejběžnější operace dotazu používá filtr ve formě logického výrazu. Dotaz pak vrátí pouze prvky, pro které je výraz pravdivý. `Where`K provedení filtrování se používá klauzule. Filtr určuje, které prvky ve zdroji dat mají být zahrnuty ve výsledné sekvenci. V následujícím příkladu jsou zahrnuti pouze zákazníci, kteří mají adresu v Londýně.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Pomocí logických operátorů, jako jsou a, můžete `And` `Or` kombinovat výrazy filtru v `Where` klauzuli. Pokud například chcete vracet pouze ty zákazníky, kteří jsou z Londýna a jejichž název je Devon, použijte následující kód:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 Chcete-li vracet zákazníky z Brna nebo Paříž, použijte následující kód:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Další informace o použití `Where` klauzule v Visual Basic naleznete v tématu [Where klauzule](../../../language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Řazení dat (Order By)  
 Často je vhodné řadit vracená data do konkrétního pořadí. `Order By`Klauzule způsobí, že prvky v vrácené sekvenci budou seřazeny podle zadaného pole nebo polí. Například následující dotaz seřadí výsledky na základě `Name` Vlastnosti. Vzhledem k tomu `Name` , že je řetězec, vrácená data budou řazena abecedně, od a do Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Pro seřazení výsledků v opačném pořadí z Z na A použijte `Order By...Descending` klauzuli. Výchozí hodnota je, `Ascending` Pokud `Ascending` `Descending` není zadána ani ani.  
  
 Další informace o použití `Order By` klauzule v Visual Basic naleznete v tématu [ORDER by klauzule](../../../language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Výběr dat (Select)  
 `Select`Klauzule určuje formulář a obsah vrácených elementů. Například můžete určit, zda budou výsledky obsahovat kompletní `Customer` objekty, pouze jednu `Customer` vlastnost, podmnožinu vlastností, kombinaci vlastností z různých zdrojů dat nebo některý nový typ výsledku na základě výpočtu. Když `Select` klauzule vytvoří jinou než kopii zdrojového elementu, operace se nazývá *projekce*.  
  
 Chcete-li načíst kolekci, která se skládá z kompletních `Customer` objektů, vyberte proměnnou rozsahu samotné:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Pokud `Customer` je instancí velký objekt, který má mnoho polí a všechny, které chcete načíst, je název, můžete vybrat `cust.Name` , jak je znázorněno v následujícím příkladu. Odvození místního typu rozpoznává, že se změní výsledný typ z kolekce `Customer` objektů na kolekci řetězců.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Chcete-li vybrat více polí ze zdroje dat, máte dvě možnosti:  
  
- V `Select` klauzuli zadejte pole, která chcete zahrnout do výsledku. Kompilátor definuje anonymní typ, který bude mít tato pole jako své vlastnosti. Další informace najdete v tématu [anonymní typy](../../language-features/objects-and-classes/anonymous-types.md).  
  
     Vzhledem k tomu, že vrácené elementy v následujícím příkladu jsou instancemi anonymního typu, nelze odkazovat na typ podle názvu jinde v kódu. Název určený pro kompilátor pro typ obsahuje znaky, které nejsou platné v normálním Visual Basic kódu. V následujícím příkladu elementy v kolekci, které jsou vráceny dotazem v, `londonCusts4` jsou instancemi anonymního typu.  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -nebo-  
  
- Definujte pojmenovaný typ obsahující konkrétní pole, která chcete zahrnout do výsledku, a v klauzuli vytvořte a inicializujte instance typu `Select` . Tuto možnost použijte pouze v případě, že je nutné použít jednotlivé výsledky mimo kolekci, ve které jsou vráceny, nebo pokud je třeba je předat jako parametry v volání metody. Typ `londonCusts5` v následujícím příkladu je IEnumerable (of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Další informace o použití `Select` klauzule v Visual Basic naleznete v tématu [Select klauzule](../../../language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Spojování dat (Join a Group Join)  
 V klauzuli můžete několik způsobů kombinovat více než jeden zdroj dat `From` . Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku. Dotaz vybírá studenty, jejichž příjmení začínají znakem samohlásky.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Tento kód můžete spustit se seznamem studentů vytvořených v tématu [Postupy: vytvoření seznamu položek](how-to-create-a-list-of-items.md).  
  
 `Join`Klíčové slovo je ekvivalentem `INNER JOIN` v SQL. Kombinuje dvě kolekce na základě shodných klíčových hodnot mezi prvky ve dvou kolekcích. Dotaz vrátí všechny prvky kolekce nebo jejich část, které mají odpovídající hodnoty klíče. Například následující kód duplikuje akci předchozího implicitního spojení.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`kombinuje kolekce do jedné hierarchické kolekce stejně jako `LEFT JOIN` v SQL. Další informace najdete v tématu [klauzule JOIN](../../../language-reference/queries/join-clause.md) a [klauzule Group Join](../../../language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Seskupování dat (Group By)  
 Můžete přidat `Group By` klauzuli pro seskupení prvků ve výsledku dotazu v závislosti na jednom nebo více polích prvků. Například následující kód seskupuje studenty podle třídy year.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Pokud spustíte tento kód pomocí seznamu studentů vytvořených v tématu [Postupy: vytvoření seznamu položek](how-to-create-a-list-of-items.md), výstup `For Each` příkazu je:  
  
 Rok: méně  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Rok: vedoucí  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Rok: čerstvá  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 Variace znázorněné v následujícím kódu řadí roky třídy a potom jednotlivé studenty vyřadí do každého roku podle příjmení.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Další informace o najdete `Group By` v tématu [klauzule GROUP by](../../../language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic.IEnumerable%601>
- [Začínáme s dotazy LINQ v jazyce Visual Basic](getting-started-with-linq.md)
- [Dotazy](../../../language-reference/queries/index.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [LINQ](../../language-features/linq/index.md)
