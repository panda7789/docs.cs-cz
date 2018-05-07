---
title: Základní operace dotazů (Visual Basic)
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
ms.openlocfilehash: 5587a60e97464324659b325e38a18ac25488d30d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="basic-query-operations-visual-basic"></a>Základní operace dotazů (Visual Basic)
Toto téma obsahuje stručný úvod do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazy v jazyce Visual Basic a některé typické druhy operace, které můžete provádět v dotazu. Další informace naleznete v následujících tématech:  
  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [Návod: Zápis dotazů v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Určení zdroje dat (From)  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, prvním krokem je určit zdroj dat, která mají být zobrazeny. Proto `From` klauzuli v dotazu vždy nastane dříve. Operátory dotazu vyberte a utvářejí výsledek závislosti na typu zdroje.  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 `From` Klauzuli určuje zdroje dat, `customers`a *proměnnou rozsahu*, `cust`. Proměnná rozsahu je jako proměnné iterace smyčky, s tím rozdílem, že ve výrazu dotazu, dojde k žádné skutečné iterací. Když je proveden dotaz, často pomocí `For Each` smyčky, proměnnou rozsahu slouží jako odkaz na všechny následné prvky v `customers`. Protože kompilátor lze odvodit typ `cust`, není nutné explicitně zadat. Příklady dotazů, které jsou zapsány s i bez explicitního zadáním najdete v tématu [vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Další informace o tom, jak používat `From` klauzule v jazyce Visual Basic, najdete v části [klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrování dat (Where)  
 Nejběžnější operace dotazů je pravděpodobně použití filtru ve formě logický výraz. Dotaz vrátí pouze elementy, pro které je výraz hodnotu true. A `Where` klauzule se používá k filtrování. Filtr určuje prvky, které ve zdroji dat chcete zahrnout do výsledné pořadí. V následujícím příkladu jsou zahrnuty pouze zákazníků, kteří mají adresu v Londýně.  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 Logické operátory můžete použít jako `And` a `Or` kombinovat výrazy filtru v `Where` klauzule. Například vrátit pouze zákazníky, kteří jsou z Londýna a jehož jméno je Devon, použijte následující kód:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Vracení zákazníky z Londýna nebo Paříž, použijte následující kód:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Další informace o tom, jak používat `Where` klauzule v jazyce Visual Basic, najdete v části [klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Řazení dat (Order By)  
 Často je vhodné seřaďte vrácená data do konkrétní pořadí. `Order By` Klauzule způsobí, že prvky ve vrácené pořadí řazení zadané pole nebo pole. Například následující dotaz seřadí výsledků na základě `Name` vlastnost. Protože `Name` je řetězec, vrácená data se řadí abecedně, od A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Chcete-li v obráceném pořadí řazení výsledků z Z až A, použijte `Order By...Descending` klauzule. Výchozí hodnota je `Ascending` při ani `Ascending` ani `Descending` je zadán.  
  
 Další informace o tom, jak používat `Order By` klauzule v jazyce Visual Basic, najdete v části [klauzuli ORDER by](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Výběr dat (Select)  
 `Select` Klauzuli určuje formuláře a obsah vrácený elementů. Například můžete určit, jestli výsledky budou tvořeny dokončení `Customer` objekty, pouze jeden `Customer` vlastnost, podmnožinu vlastností, kombinace vlastnosti z různých zdrojů dat. nebo nový typ výsledku na základě výpočtu. Když `Select` klauzule vytvořil něco jiného než kopii source element, operace se nazývá *projekce*.  
  
 Načtení kolekce, která se skládá z dokončení `Customer` objektů, vyberte proměnnou rozsahu, sám sebe:  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 Pokud `Customer` instance je rozsáhlý objekt, který má mnoho polí a všechno, co můžete obnovit je název, můžete vybrat `cust.Name`, jak je znázorněno v následujícím příkladu. Odvození místního typu rozpozná, že to změní typ výsledku z kolekce `Customer` objekty do kolekce řetězců.  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 Pokud chcete vybrat více polí ze zdroje dat, máte dvě možnosti:  
  
-   V `Select` klauzuli určujete pole, které chcete zahrnout do výsledku. Kompilátor definují anonymní typ, který má tato pole jako jeho vlastnosti. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Protože vrácené prvky v následujícím příkladu jsou instancemi anonymního typu, nelze odkazovat na typ podle názvu někde v kódu. Název kompilátoru určeno pro typ obsahuje znaky, které nejsou platné v normálním kód jazyka Visual Basic. V následujícím příkladu, elementů v kolekci, která je vrácených dotazem v `londonCusts4` jsou instancemi anonymního typu  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     -nebo-  
  
-   Definování typu s názvem, který obsahuje konkrétní pole, které chcete zahrnout do výsledku a vytvoření a Inicializace instance typu ve `Select` klauzule. Tuto možnost použijte jenom v případě, že budete muset použít jednotlivé výsledky mimo kolekce, ve kterém jsou vráceny, nebo pokud máte předejte jako parametry volání metod. Typ `londonCusts5` v následujícím příkladu je rozhraní IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Další informace o tom, jak používat `Select` klauzule v jazyce Visual Basic, najdete v části [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Spojování dat (Join a Group Join)  
 Můžete kombinovat více než jeden zdroj dat v `From` klauzule několika způsoby. Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku. Dotaz vybere studenty, jejichž příjmení začínají samohláskou.  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  Tento kód můžete spustit pomocí seznamu studenty vytvořené v [postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 `Join` – Klíčové slovo je ekvivalentní `INNER JOIN` v systému SQL. Kombinuje dvě kolekce založené na odpovídající hodnoty klíče mezi elementy v dvě kolekce. Dotaz vrátí nebo její část elementů kolekce, které mají odpovídající hodnoty klíče. Následující kód například duplikuje akce předchozí implicitní spojení.  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` kombinuje kolekce do jedné kolekce hierarchické, podobně jako `LEFT JOIN` v systému SQL. Další informace najdete v tématu [klauzuli Join](../../../../visual-basic/language-reference/queries/join-clause.md) a [Group Join – klauzule](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Seskupování dat (Group By)  
 Můžete přidat `Group By` klauzule k seskupení elementy ve výsledku dotazu podle jednoho nebo více polí elementů. Následující kód například skupiny studenty pomocí třídy roku.  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 Pokud spustíte tento kód pomocí seznamu studenty vytvořené v [postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), výstup `For Each` příkaz je:  
  
 Rok: nižší  
  
 Tucker, Michael  
  
 Garcia Hugo  
  
 Garcia Debra  
  
 Tucker Lance  
  
 Rok: Senior  
  
 Omelchenko Svetlana  
  
 Novák, Michiko  
  
 Fakhouri Fadi  
  
 Feng Hanying  
  
 Adams Terry  
  
 Rok: Freshman  
  
 Mortensen Sven  
  
 Garcia Cesaru  
  
 Variaci vidět v následujícím kódu řadí let třídy a pak objednávky na studentů v rámci každý rok podle příjmení.  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 Další informace o `Group By`, najdete v části [skupiny pomocí klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
