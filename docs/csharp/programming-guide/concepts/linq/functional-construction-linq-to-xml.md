---
title: Funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635753"
---
# <a name="functional-construction-linq-to-xml-c"></a>Funkční konstrukce (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje účinný způsob vytváření elementů XML nazývaných *funkční konstrukce*. Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.  
  
 Existuje několik klíčových [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkcí programovacího rozhraní, které umožňují funkční konstrukci:  
  
- Konstruktor <xref:System.Xml.Linq.XElement> má různé typy argumentů pro obsah. Můžete například předat <xref:System.Xml.Linq.XElement> jiný objekt, který se stane podřízeným prvkem. Můžete předat <xref:System.Xml.Linq.XAttribute> objekt, který se stane atributem prvku. Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a stane se textovým obsahem prvku.  
  
- Konstruktor <xref:System.Xml.Linq.XElement> přebírá `params` pole typu <xref:System.Object>, takže můžete předat libovolný počet objektů konstruktoru. To umožňuje vytvořit prvek, který má komplexní obsah.  
  
- Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekce v objektu je výčtu a jsou přidány všechny položky v kolekci. Pokud kolekce <xref:System.Xml.Linq.XElement> obsahuje <xref:System.Xml.Linq.XAttribute> nebo objekty, každá položka v kolekci je přidán samostatně. To je důležité, protože umožňuje předat výsledky dotazu LINQ konstruktoru.  
  
 Tyto funkce umožňují psát kód pro vytvoření stromu XML. Například:  
  
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
  
 Tyto funkce také umožňují psát kód, který používá výsledky dotazů LINQ při vytváření stromu XML, a to následovně:  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  