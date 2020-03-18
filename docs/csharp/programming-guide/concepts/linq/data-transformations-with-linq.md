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
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635948"
---
# <a name="data-transformations-with-linq-c"></a>Transformace dat pomocí LINQ (C#)
Jazykově integrovaný dotaz (LINQ) není jen o načítání dat. Je to také mocný nástroj pro transformaci dat. Pomocí dotazu LINQ můžete použít zdrojovou sekvenci jako vstup a upravit ji mnoha způsoby k vytvoření nové výstupní sekvence. Samotnou sekvenci můžete upravit bez úprav samotných prvků řazením a seskupováním. Ale možná nejsilnější funkce linq dotazů je schopnost vytvářet nové typy. To je dosaženo v [select](../../../language-reference/keywords/select-clause.md) klauzule. Můžete například provádět následující úkoly:  
  
- Sloučit více vstupních sekvencí do jedné výstupní sekvence, která má nový typ.  
  
- Vytvořte výstupní sekvence, jejichž prvky se skládají pouze z jedné nebo několika vlastností každého prvku ve zdrojové sekvenci.  
  
- Vytvořte výstupní sekvence, jejichž prvky se skládají z výsledků operací prováděných na zdrojových datech.  
  
- Vytvořte výstupní sekvence v jiném formátu. Můžete například transformovat data z řádků SQL nebo textových souborů do xml.  
  
 To je jen několik příkladů. Samozřejmě tyto transformace lze kombinovat různými způsoby ve stejném dotazu. Kromě toho výstupní sekvence jednoho dotazu lze použít jako vstupní sekvence pro nový dotaz.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Spojování více vstupů do jedné výstupní sekvence  
 Dotaz LINQ můžete použít k vytvoření výstupní sekvence, která obsahuje prvky z více než jedné vstupní sekvence. Následující příklad ukazuje, jak kombinovat dvě datové struktury v paměti, ale stejné principy lze použít ke kombinování dat ze zdrojů XML nebo SQL nebo DataSet. Předpokládejme následující dva typy tříd:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 Následující příklad ukazuje dotaz:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Další informace naleznete v [tématu join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Výběr podmnožiny jednotlivých zdrojových elementů  
 Existují dva primární způsoby, jak vybrat podmnožinu každého prvku ve zdrojové sekvenci:  
  
1. Chcete-li vybrat pouze jeden člen zdrojového prvku, použijte tečkovou operaci. V následujícím příkladu předpokládejme, že `Customer` objekt obsahuje `City`několik veřejných vlastností včetně řetězce s názvem . Při spuštění tohoto dotazu vytvoří výstupní posloupnost řetězců.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Chcete-li vytvořit prvky, které obsahují více než jednu vlastnost ze zdrojového prvku, můžete použít inicializátor objektu s pojmenovaným objektem nebo anonymním typem. Následující příklad ukazuje použití anonymního typu k zapouzdření dvou vlastností z každého `Customer` prvku:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Další informace naleznete v [tématu Objekt a kolekce Inicializátory](../../classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Transformace objektů v paměti do jazyka XML  
 Dotazy LINQ usnadňují transformaci dat mezi datovými strukturami v paměti, databázemi SQL, ADO.NET datovými sadami a datovými proudy XML nebo dokumenty. Následující příklad transformuje objekty v datové struktuře v paměti na elementy XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 Kód vytváří následující výstup XML:  
  
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
  
 Další informace naleznete [v tématu Creating XML Trees in C# (LINQ to XML).](./creating-xml-trees-linq-to-xml-2.md)  
  
## <a name="performing-operations-on-source-elements"></a>Provádění operací se zdrojovými elementy  
 Výstupní sekvence nemusí obsahovat žádné prvky nebo vlastnosti elementu ze zdrojové sekvence. Výstup může být místo toho posloupnost hodnot, která je vypočítána pomocí zdrojových prvků jako vstupních argumentů. Následující jednoduchý dotaz, když je spuštěn, výstupy posloupnost řetězců, jejichž hodnoty představují výpočet `double`na základě zdrojové sekvence prvků typu .  
  
> [!NOTE]
> Volání metod ve výrazech dotazu není podporováno, pokud bude dotaz přeložen do jiné domény. Například nelze volat běžné c# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] metoda v protože SQL Server nemá žádný kontext pro něj. Uložené procedury však můžete mapovat na metody a volat je. Další informace naleznete [v tématu Uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Viz také

- [Dotaz integrovaný jazykem (LINQ) (C#)](./index.md)
- [Technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ do XML (C#)](./linq-to-xml-overview.md)
- [Výrazy dotazu LINQ](../../../linq/index.md)
- [select – klauzule](../../../language-reference/keywords/select-clause.md)
