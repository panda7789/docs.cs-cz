---
title: Transformace dat pomocí LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: be488b262764480b519e291727a21830d7a18e8f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201427"
---
# <a name="data-transformations-with-linq-c"></a>Transformace dat pomocí LINQ (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] není jenom o načítání dat Je také výkonné nástroje pro transformaci dat. Pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, můžete použít zdrojové sekvence, stejně jako vstup a upravit v mnoha způsoby, jak vytvořit nové pořadí výstupu. Můžete změnit pořadí samotné beze změny samotné prvky řazení a seskupení. Ale možná procesorově nejvýkonnější funkce [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů je schopnost vytvářet nové typy. To lze provést v [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli. Například můžete provádět následující úlohy:  
  
-   Na jednu výstupní sekvenci, která má nový typ sloučení více vstupních sekvencí.  
  
-   Vytvoření výstupní sekvence, jehož prvky jsou tvořeny pouze jednu nebo několik vlastností jednotlivých prvků ve zdrojové sekvenci.  
  
-   Výstup pořadí, jehož prvky jsou tvořeny výsledky operace provedené na zdroj dat vytvořte.  
  
-   Vytváření pořadí výstup do jiného formátu. Například můžete transformovat data z SQL řádků nebo textové soubory do souboru XML.  
  
 Toto jsou jen několik příkladů. Samozřejmě tyto transformace zkombinovat ve stejném dotazu různými způsoby. Kromě toho výstup posloupnost jeden dotaz slouží jako vstupní sekvence pro nový dotaz.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Spojování více vstupů do jedné výstupní sekvence  
 Můžete použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, který vytvořit výstupní sekvenci, která obsahuje elementy z více než jeden vstupní sekvence. Následující příklad ukazuje, jak kombinovat dvě struktury dat v paměti, ale stejné zásady můžete použít u kombinovat data ze zdroje XML nebo SQL nebo datové sady. Předpokládejme následující typy dvou tříd:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 Následující příklad ukazuje dotaz:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Další informace najdete v tématu [klauzule join](../../../../csharp/language-reference/keywords/join-clause.md) a [klauzule select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Výběr podmnožiny jednotlivých zdrojových elementů  
 Existují dva základní způsoby, které vyberou podmnožinu každý prvek ve zdrojové sekvenci:  
  
1.  Vybrat jen jeden člen zdrojového prvku, pomocí operace tečkou. V následujícím příkladu se předpokládá, že `Customer` objekt obsahuje několik veřejných vlastností, včetně řetězec s názvem `City`. Při spuštění, tento dotaz vytvoří výstup posloupnost řetězců.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  Pokud chcete vytvořit prvky, které obsahují více než jednu vlastnost ze zdrojového elementu, můžete inicializátoru objektu pojmenovaný objekt nebo anonymního typu. Následující příklad ukazuje použití anonymní typ k zapouzdření dvě vlastnosti z každého `Customer` element:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Další informace najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Transformace objektů v paměti do jazyka XML  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy umožňují snadno transformovat data mezi struktury dat v paměti, databází SQL, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datové sady a XML datových proudů nebo dokumenty. V následujícím příkladu transformace objektů v struktury dat v paměti do elementů XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 Kód vytvoří následující výstup XML:  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Další informace najdete v tématu [vytváření stromů XML v jazyce C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Provádění operací se zdrojovými elementy  
 Výstupní sekvenci nemusí obsahovat všechny prvky nebo element vlastnosti ze zdrojové sekvence. Výstup může být místo toho sekvenci hodnot, které je vypočítán s použitím zdrojové prvky jako vstupní argumenty. Následující jednoduchý dotaz, pokud je spuštěn, výstupy sekvencí řetězců, jehož hodnoty představují podle zdrojové sekvence prvků typu výpočtu `double`.  
  
> [!NOTE]
>  Volání metody ve výrazech dotazů není podporováno, pokud dotaz bude fungovat některé jiné domény. Například nelze volat běžné metody jazyka C# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] vzhledem k tomu, že systém SQL Server nemá žádný kontext pro něj. Můžete ale mapování uložené procedury k metodám a volat. Další informace najdete v tématu [uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Viz také:

- [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [Technologie LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
- [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [select – klauzule](../../../../csharp/language-reference/keywords/select-clause.md)
