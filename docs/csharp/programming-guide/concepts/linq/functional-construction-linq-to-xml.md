---
title: Funkční konstrukce (LINQ to XML) (C#)
description: Přečtěte si, jak rozhraní pro programování LINQ to XML umožňuje vytváření funkčního stromu, schopnost vytvořit strom XML v jednom příkazu v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103773"
---
# <a name="functional-construction-linq-to-xml-c"></a>Funkční konstrukce (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje účinný způsob, jak vytvořit prvky XML nazvané *funkční konstrukce*. Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.  
  
 Existuje několik klíčových funkcí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovacího rozhraní, které umožňují konstrukci funkčnosti:  
  
- <xref:System.Xml.Linq.XElement>Konstruktor přijímá různé typy argumentů pro obsah. Například můžete předat další <xref:System.Xml.Linq.XElement> objekt, který se stal podřízeným prvkem. Můžete předat <xref:System.Xml.Linq.XAttribute> objekt, který se stal atributem elementu. Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a který se změní na textový obsah elementu.  
  
- <xref:System.Xml.Linq.XElement>Konstruktor přebírá `params` pole typu <xref:System.Object> , aby bylo možné předat do konstruktoru libovolný počet objektů. To umožňuje vytvořit prvek, který má složitý obsah.  
  
- Pokud objekt implementuje, je vyhodnocena <xref:System.Collections.Generic.IEnumerable%601> kolekce v objektu a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje <xref:System.Xml.Linq.XElement> objekty nebo <xref:System.Xml.Linq.XAttribute> , každá položka v kolekci se přidá samostatně. To je důležité, protože umožňuje předat výsledky dotazu LINQ do konstruktoru.  
  
 Tyto funkce umožňují napsat kód pro vytvoření stromu XML. Například:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Tyto funkce také umožňují napsat kód, který používá výsledky dotazů LINQ při vytváření stromu XML takto:  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  