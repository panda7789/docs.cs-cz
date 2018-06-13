---
title: Funkční konstrukce (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: c837660adf9c62c8f4304b92d37f732795c981c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329852"
---
# <a name="functional-construction-linq-to-xml-c"></a>Funkční konstrukce (technologie LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nabízí efektivní způsob, jak vytvořit elementů XML s názvem *funkční konstrukce*. Funkční konstrukce je schopnost vytvářet strom XML v jediném příkazu.  
  
 Existuje několik klíčových funkcích služby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní, které povolit funkční konstrukce:  
  
-   <xref:System.Xml.Linq.XElement> Konstruktor přebírá různé typy argumentů pro obsah. Můžete například předat jiné <xref:System.Xml.Linq.XElement> objekt, který se stane podřízený element. Můžete předat <xref:System.Xml.Linq.XAttribute> objektu, který bude atribut elementu. Nebo můžete předat jiný typ objektu, který je převedeno na řetězec a že bude textového obsahu elementu.  
  
-   <xref:System.Xml.Linq.XElement> Konstruktor přijímá `params` pole typu <xref:System.Object>, takže můžete předat libovolný počet objektů do konstruktoru. Umožňuje vytvořit element, který má složitý obsah.  
  
-   Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu, a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně. To je důležité, protože vám umožňuje předat výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu konstruktoru.  
  
 Tyto funkce umožňují napsat kód pro vytvoření strom XML. Následuje příklad:  
  
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
  
 Tyto funkce umožňují taky napsat kód, který používá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazuje při vytváření strom XML následujícím způsobem:  
  
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
  
## <a name="see-also"></a>Viz také  
 [Vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
