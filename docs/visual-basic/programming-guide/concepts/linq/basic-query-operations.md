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
ms.openlocfilehash: ed5ed56366911c3676c4413711207ac0a8f85765
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925645"
---
# <a name="basic-query-operations-visual-basic"></a>Základní operace dotazů (Visual Basic)
Toto téma nabízí stručný úvod do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazy v jazyce Visual Basic a některé typické druhy operací, které provedete v dotazu. Další informace naleznete v následujících tématech:  
  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Dotazy](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Návod: Zápis dotazů v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Určení zdroje dat (From)  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, prvním krokem je určení zdroje dat, který chcete zadat dotaz. Proto `From` klauzule v dotazu vždy nastane dřív. Operátory dotazu vyberte a tvar výsledku založená na typu zdroje.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From` Klauzule určuje zdroje dat, `customers`a *proměnnou rozsahu*, `cust`. Proměnná rozsahu je jako proměnné iterace smyčky, s tím rozdílem, že ve výrazu dotazu, dojde k žádné skutečné iterace. Při spuštění dotazu, často pomocí `For Each` smyčky, proměnná rozsahu slouží jako odkaz na každý prvek po sobě jdoucích `customers`. Protože kompilátor může odvodit typ `cust`, není potřeba explicitně zadat. Příklady dotazů zapisovat a nemusíte explicitní zadání, najdete v článku [vztahy typů v operacích dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Další informace o tom, jak používat `From` klauzule v jazyce Visual Basic naleznete v tématu [klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrování dat (Where)  
 Pravděpodobně nejběžnější operace dotazu je použití filtru ve formě logický výraz. Dotaz vrátí pouze prvky, pro které má výraz hodnotu true. A `Where` klauzule se používá k provedení filtrování. Filtr určuje prvky, které ve zdroji dat chcete zahrnout do výsledné pořadí. V následujícím příkladu jsou zahrnuty pouze zákazníci, kteří mají adresu v Londýně.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Můžete například použít logické operátory `And` a `Or` kombinování výrazů filtru v `Where` klauzuli. Například pokud chcete vrátit pouze tito zákazníci, kteří jsou z Londýna a jejíž název je Devon, použijte následující kód:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Chcete-li vrátit zákazníci z Londýna nebo Paříž, použijte následující kód:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Další informace o tom, jak používat `Where` klauzule v jazyce Visual Basic naleznete v tématu [klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Řazení dat (Order By)  
 Často je vhodné seřaďte vrácená data do určitého pořadí. `Order By` Klauzule způsobí prvky ve vrácené posloupnosti, která má být seřazená podle určitého pole nebo pole. Například následující dotaz řadí výsledky podle `Name` vlastnost. Protože `Name` je řetězec, vrácená data se budou řadit abecedně, z A do Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Chcete-li v obráceném pořadí řazení výsledků od Z do A, použijte `Order By...Descending` klauzuli. Výchozí hodnota je `Ascending` při ani `Ascending` ani `Descending` je zadán.  
  
 Další informace o tom, jak používat `Order By` klauzule v jazyce Visual Basic naleznete v tématu [klauzuli ORDER by](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Výběr dat (Select)  
 `Select` Klauzule určuje formulář opravdu zavřít a obsah vrácených prvků. Například můžete určit, zda vaše výsledky se skládají z kompletní `Customer` objekty jen jeden `Customer` vlastnosti, podmnožinu vlastností, kombinací vlastností z různých zdrojů dat, nebo nový typ výsledku na základě výpočtu. Když `Select` klauzule vytváří něco jiného než kopii zdrojového elementu, operace se nazývá *projekce*.  
  
 K načtení kolekce, která se skládá z kompletní `Customer` objektů, vyberte vlastní proměnnou rozsahu:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Pokud `Customer` instance je velký objekt, který má velký počet polí, a vše, co chcete načíst je název, můžete vybrat `cust.Name`, jak je znázorněno v následujícím příkladu. Odvození místního typu rozpozná, že změní typ výsledku z kolekce `Customer` objekty kolekce řetězců.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Pokud chcete vybrat více polí ze zdroje dat, máte dvě možnosti:  
  
- V `Select` klauzule, určete pole, které chcete zahrnout do výsledku. Kompilátor bude definovat anonymní typ, který má tato pole jako její vlastnosti. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Protože vrácených prvků v následujícím příkladu jsou instancemi anonymního typu, nelze odkazovat na typ podle názvu jinde ve vašem kódu. Název typu určen kompilátor obsahuje znaky, které nejsou platné v normální kódu jazyka Visual Basic. V následujícím příkladu elementů v kolekci, která je vrácena dotazem v `londonCusts4` jsou instancemi anonymního typu  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -nebo-  
  
- Definování typu s názvem, který obsahuje konkrétní pole, které chcete zahrnout do výsledku a vytváření a inicializace instancí typu `Select` klauzuli. Tuto možnost použijte jenom v případě, že budete muset použít jednotlivé výsledky mimo kolekce, ve kterém jsou vráceny, nebo pokud musíte předat jako parametry volání metody. Typ `londonCusts5` v následujícím příkladu je IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Další informace o tom, jak používat `Select` klauzule v jazyce Visual Basic naleznete v tématu [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Spojování dat (Join a Group Join)  
 Můžete zkombinovat více než jeden zdroj dat v `From` klauzule několika způsoby. Například následující kód používá dva zdroje dat a implicitně kombinuje vlastnosti z obou z nich ve výsledku. Dotaz vybere studenty, jejichž příjmení začínají samohláskou.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  Můžete spustit tento kód se seznamem studenti vytvořili v [jak: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 `Join` – Klíčové slovo je ekvivalentní `INNER JOIN` v SQL. Kombinuje dvě kolekce založené na odpovídající hodnoty klíče mezi prvky ve dvou kolekcích. Dotaz vrátí všechny nebo část elementů kolekce, které mají odpovídající hodnoty klíče. Například následující kód duplikuje akce předchozí implicitní spojení.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` kombinuje kolekce do jedné hierarchické kolekce, stejně jako `LEFT JOIN` v SQL. Další informace najdete v tématu [Klauzule Join](../../../../visual-basic/language-reference/queries/join-clause.md) a [Group Join – klauzule](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Seskupování dat (Group By)  
 Můžete přidat `Group By` klauzule seskupit elementy ve výsledku dotazu podle polí jednoho nebo více prvků. Následující kód například skupiny studentů podle roku třídy.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Pokud jste spuštění tohoto kódu pomocí seznamu studentů vytvořené v [jak: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), výstup `For Each` příkaz je:  
  
 Rok: Nižší  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia Debra  
  
 Tucker Lance  
  
 Rok: Senior  
  
 Omelchenko Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Rok: Freshman  
  
 Mortensen Sven  
  
 Garcia Cesarovi  
  
 Varianta je znázorněno v následujícím kódu orders let třídy a pak podle příjmení orders studenty v rámci každý rok.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Další informace o `Group By`, naleznete v tématu [klauzule Group](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic.IEnumerable%601>
- [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
