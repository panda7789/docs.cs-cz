---
title: Funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635753"
---
# <a name="functional-construction-linq-to-xml-c"></a>Funkční konstrukce (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje účinný způsob, jak vytvořit prvky XML nazvané *funkční konstrukce*. Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.  
  
 Existuje několik klíčových funkcí rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, které umožňují konstrukci funkčnosti:  
  
- Konstruktor <xref:System.Xml.Linq.XElement> přebírá různé typy argumentů pro obsah. Například můžete předat další objekt <xref:System.Xml.Linq.XElement>, který se stal podřízeným prvkem. Můžete předat objekt <xref:System.Xml.Linq.XAttribute>, který se stal atributem elementu. Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a který se změní na textový obsah elementu.  
  
- Konstruktor <xref:System.Xml.Linq.XElement> přebírá `params` pole typu <xref:System.Object>, takže můžete konstruktoru předat libovolný počet objektů. To umožňuje vytvořit prvek, který má složitý obsah.  
  
- Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vyhodnocena kolekce v objektu a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje objekty <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, každá položka v kolekci se přidá samostatně. To je důležité, protože umožňuje předat výsledky dotazu LINQ do konstruktoru.  
  
 Tyto funkce umožňují napsat kód pro vytvoření stromu XML. Tady je příklad:  
  
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
  