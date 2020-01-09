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
ms.openlocfilehash: b9216dba23f49e4d9fd99687e38f5c13addde8fb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636871"
---
# <a name="basic-query-operations-visual-basic"></a>Základní operace dotazů (Visual Basic)
Toto téma poskytuje stručný úvod do výrazů LINQ (Language-Integrated Query) v Visual Basic a na některé běžné druhy operací, které v dotazu provedete. Další informace naleznete v následujících tématech:  
  
 [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Dotazy](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Návod: zápis dotazů v Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Určení zdroje dat (From)  
 V dotazu LINQ je prvním krokem určení zdroje dat, který chcete dotazovat. Proto je klauzule `From` v dotazu vždy první. Operátory dotazu vyberou a tvarují výsledek na základě typu zdroje.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 Klauzule `From` Určuje zdroj dat, `customers`a *proměnnou rozsahu*`cust`. Proměnná rozsahu je jako proměnná iterace smyčky, s výjimkou toho, že ve výrazu dotazu není k dispozici žádná skutečná iterace. Při spuštění dotazu, často pomocí `For Each` smyčky, proměnná rozsahu slouží jako odkaz na každý po sobě jdoucí prvek v `customers`. Protože kompilátor může odvodit typ `cust`, nemusíte ho explicitně určovat. Příklady dotazů napsaných pomocí a bez explicitního zadávání najdete v tématu [vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Další informace o použití klauzule `From` v Visual Basic naleznete v části [from klauzule](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrování dat (Where)  
 Pravděpodobně nejběžnější operace dotazu používá filtr ve formě logického výrazu. Dotaz pak vrátí pouze prvky, pro které je výraz pravdivý. K provedení filtrování se používá klauzule `Where`. Filtr určuje, které prvky ve zdroji dat mají být zahrnuty ve výsledné sekvenci. V následujícím příkladu jsou zahrnuti pouze zákazníci, kteří mají adresu v Londýně.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Pomocí logických operátorů, jako je například `And` a `Or`, lze kombinovat výrazy filtru v klauzuli `Where`. Pokud například chcete vracet pouze ty zákazníky, kteří jsou z Londýna a jejichž název je Devon, použijte následující kód:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Chcete-li vracet zákazníky z Brna nebo Paříž, použijte následující kód:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Další informace o použití klauzule `Where` v Visual Basic naleznete v tématu [Where klauzule](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Řazení dat (Order By)  
 Často je vhodné řadit vracená data do konkrétního pořadí. Klauzule `Order By` způsobí, že prvky v vrácené sekvenci budou seřazeny podle zadaného pole nebo polí. Například následující dotaz seřadí výsledky na základě vlastnosti `Name`. Vzhledem k tomu, že `Name` je řetězec, vrácená data budou řazena abecedně, od A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Pro seřazení výsledků v opačném pořadí z Z na a použijte klauzuli `Order By...Descending`. Výchozí hodnota je `Ascending`, pokud není zadána žádná `Ascending` ani `Descending`.  
  
 Další informace o použití klauzule `Order By` v Visual Basic naleznete v tématu [ORDER by klauzule](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Výběr dat (Select)  
 Klauzule `Select` určuje formulář a obsah vrácených elementů. Například můžete určit, zda budou výsledky tvořit kompletní `Customer` objekty, jenom jednu `Customer` vlastnost, podmnožinu vlastností, kombinaci vlastností z různých zdrojů dat nebo některý nový typ výsledku na základě výpočtu. Když klauzule `Select` vytvoří jinou než kopii zdrojového elementu, operace se nazývá *projekce*.  
  
 Chcete-li načíst kolekci, která se skládá z kompletních objektů `Customer`, vyberte proměnnou rozsahu:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Pokud je instance `Customer` velký objekt, který má mnoho polí a všechny, které chcete načíst, je název, můžete vybrat `cust.Name`, jak je znázorněno v následujícím příkladu. Odvození místního typu rozpoznává, že se změní výsledný typ z kolekce `Customer` objektů na kolekci řetězců.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Chcete-li vybrat více polí ze zdroje dat, máte dvě možnosti:  
  
- V klauzuli `Select` zadejte pole, která chcete zahrnout do výsledku. Kompilátor definuje anonymní typ, který bude mít tato pole jako své vlastnosti. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Vzhledem k tomu, že vrácené elementy v následujícím příkladu jsou instancemi anonymního typu, nelze odkazovat na typ podle názvu jinde v kódu. Název určený pro kompilátor pro typ obsahuje znaky, které nejsou platné v normálním Visual Basic kódu. V následujícím příkladu jsou elementy v kolekci, které jsou vráceny dotazem v `londonCusts4` instance anonymního typu.  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -nebo-  
  
- Definujte pojmenovaný typ, který obsahuje konkrétní pole, která chcete zahrnout do výsledku, a vytvořte a inicializujte instance typu v klauzuli `Select`. Tuto možnost použijte pouze v případě, že je nutné použít jednotlivé výsledky mimo kolekci, ve které jsou vráceny, nebo pokud je třeba je předat jako parametry v volání metody. Typ `londonCusts5` v následujícím příkladu je IEnumerable (of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Další informace o použití klauzule `Select` v Visual Basic naleznete v tématu [Select klauzule](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Spojování dat (Join a Group Join)  
 V několika způsobech můžete zkombinovat více než jeden zdroj dat v klauzuli `From`. Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku. Dotaz vybírá studenty, jejichž příjmení začínají znakem samohlásky.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Tento kód můžete spustit se seznamem studentů vytvořených v tématu [Postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Klíčové slovo `Join` je ekvivalentní `INNER JOIN` v SQL. Kombinuje dvě kolekce na základě shodných klíčových hodnot mezi prvky ve dvou kolekcích. Dotaz vrátí všechny prvky kolekce nebo jejich část, které mají odpovídající hodnoty klíče. Například následující kód duplikuje akci předchozího implicitního spojení.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` kombinuje kolekce do jedné hierarchické kolekce, stejně jako `LEFT JOIN` v SQL. Další informace najdete v tématu [klauzule JOIN](../../../../visual-basic/language-reference/queries/join-clause.md) a [klauzule Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Seskupování dat (Group By)  
 Můžete přidat klauzuli `Group By` pro seskupení prvků ve výsledku dotazu podle jednoho nebo více polí prvků. Například následující kód seskupuje studenty podle třídy year.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Pokud spustíte tento kód pomocí seznamu studentů vytvořených v tématu [Postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), výstup z příkazu `For Each` je:  
  
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
  
 Další informace o `Group By`naleznete v tématu [Group by klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic.IEnumerable%601>
- [Začínáme pomocí LINQ v Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
