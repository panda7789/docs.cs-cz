---
title: "Transformace dat pomocí LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0633e348c762879caa4e3f72a3662722b3894e4c
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="data-transformations-with-linq-c"></a>Transformace dat pomocí LINQ (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]není jenom o načtení dat. Je také výkonný nástroj pro převod data. Pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, můžete použít zdrojové sekvence jako vstup a upravit v mnoho způsobů, jak vytvořit nové pořadí výstup. Můžete upravit pořadí samotné beze změny samotné prvky řazení a seskupování. Ale možná nejúčinnějších funkci [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy je schopnost vytvářet nové typy. To lze provést v [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzule. Například můžete provádět následující úlohy:  
  
-   Sloučit více vstupních sekvencí do jediného výstupu pořadí, které má nového typu.  
  
-   Vytvoření výstupní pořadí, jehož elementy obsahovat pouze jednu nebo několik vlastností jednotlivých prvků v zdrojové sekvence.  
  
-   Výstup pořadí, jehož elementy jsou tvořeny výsledky operace provedené na zdroji dat vytvořte.  
  
-   Vytvořte pořadí výstup do jiného formátu. Například můžete převést data z textových souborů nebo SQL řádků do souboru XML.  
  
 Jsou to jenom několik příkladů. Samozřejmě tyto transformace lze spojovat různými způsoby v jednom dotazu. Kromě toho výstup pořadí jeden dotaz slouží jako vstupní pořadí pro nový dotaz.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Spojování více vstupů do jedné výstupní sekvence  
 Můžete použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz k vytvoření výstupní sekvenci, která obsahuje elementy z více než jeden vstupní pořadí. Následující příklad ukazuje, jak kombinovat dvě struktury dat v paměti, ale lze použít stejné zásady kombinovat data ze zdroje XML nebo SQL nebo datovou sadu. Předpokládejme následující typy dvě třídy:  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 Následující příklad ukazuje dotaz:  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 Další informace najdete v tématu [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md) a [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Výběr podmnožiny jednotlivých zdrojových elementů  
 Existují dva způsoby primární vybrat podmnožinu každý prvek v pořadí zdroje:  
  
1.  Vyberte pouze jednu členem source element, použijte operaci tečkou. V následujícím příkladu předpokládáme, že `Customer` objekt obsahuje několik veřejné vlastnosti včetně řetězec s názvem `City`. Po provedení tohoto dotazu vytvoří v výstupní sekvenci řetězců.  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  K vytváření prvků, které obsahují více než jednu vlastnost z source element, můžete použít buď objekt s názvem, nebo anonymní typ inicializátoru objektu. Následující příklad ukazuje použití anonymní typ k zapouzdření dvě vlastnosti z každé `Customer` element:  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Další informace najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Transformace objektů v paměti do jazyka XML  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]dotazy usnadňují transformace dat mezi v paměti datové struktury, databází SQL, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datových sad a XML datové proudy nebo dokumenty. Následující příklad transformuje objekty v strukturu dat v paměti do elementů XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
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
 Výstupní sekvenci nemusí obsahovat všechny prvky nebo vlastností elementů ze zdrojové sekvence. Výstup může být místo toho pořadí hodnot, který se počítá pomocí zdrojové elementy jako vstupní argumenty. Tento jednoduchý dotaz, při spuštění, výstupy posloupnosti řetězců, jejichž hodnoty představují výpočtu podle pořadí zdrojové elementy typu `double`.  
  
> [!NOTE]
>  Volání metody ve výrazech dotazů není podporováno, pokud dotaz bude převeden na některé jiné domény. Například nelze volat obyčejnou metoda C# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] protože SQL Server nemá žádný kontext pro ni. Můžete však mapovat uložené procedury metody a ty volání. Další informace najdete v tématu [uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [Technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
 [Technologie LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Select – klauzule](../../../../csharp/language-reference/keywords/select-clause.md)
