---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4794e4fe019b30d8f2acb3eb255bb77ba2f7f290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169542"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Vytváření stromů XML v jazyce C# (LINQ to XML)
Tato část obsahuje informace o vytváření stromů XML v jazyce C#.  
  
 Informace o použití výsledků dotazů LINQ jako <xref:System.Xml.Linq.XElement>obsahu pro , naleznete v tématu [funkční konstrukce (LINQ na XML) (C#)](./functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Vytváření prvků
 Podpisy <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňují předat obsah prvku nebo atributjako argumenty konstruktoru. Vzhledem k tomu, že jeden z konstruktorů má proměnný počet argumentů, můžete předat libovolný počet podřízených prvků. Samozřejmě, každý z těchto podřízených prvků může obsahovat své vlastní podřízené prvky. Pro libovolný prvek můžete přidat libovolný počet atributů.  
  
 Při <xref:System.Xml.Linq.XNode> přidávání <xref:System.Xml.Linq.XElement>(včetně) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud nový obsah nemá nadřazený obsah, objekty jsou jednoduše připojeny ke stromu XML. Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, nový obsah je klonován a nově klonovaný obsah je připojen ke stromu XML. Poslední příklad v tomto tématu ukazuje toto.  
  
 Chcete-li `contacts` <xref:System.Xml.Linq.XElement>vytvořit , můžete použít následující kód:  
  
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
  
 Pokud je správně odsazeno, kód pro vytvoření <xref:System.Xml.Linq.XElement> objektů se velmi podobá struktuře podkladového XML.  
  
## <a name="xelement-constructors"></a>Konstruktory XElement  
 Třída <xref:System.Xml.Linq.XElement> používá následující konstruktory pro funkční konstrukci. Všimněte si, že existují <xref:System.Xml.Linq.XElement>některé další konstruktory pro , ale protože nejsou použity pro funkční konstrukce nejsou uvedeny zde.  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Vytvoří <xref:System.Xml.Linq.XElement>. Parametr `name` určuje název prvku; `content` určuje obsah prvku.|  
|`XElement(XName name)`|Vytvoří <xref:System.Xml.Linq.XElement> s <xref:System.Xml.Linq.XName> jeho inicializována na zadaný název.|  
|`XElement(XName name, params object[] content)`|Vytvoří <xref:System.Xml.Linq.XElement> s <xref:System.Xml.Linq.XName> jeho inicializována na zadaný název. Atributy nebo podřízené prvky jsou vytvořeny z obsahu seznamu parametrů.|  
  
 Parametr `content` je velmi flexibilní. Podporuje jakýkoli typ objektu, který je <xref:System.Xml.Linq.XElement>platný podřízený . Následující pravidla platí pro různé typy objektů předaných v tomto parametru:  
  
- Řetězec je přidán jako textový obsah.  
  
- Je <xref:System.Xml.Linq.XElement> přidán jako podřízený prvek.  
  
- Je <xref:System.Xml.Linq.XAttribute> přidán jako atribut.  
  
- A <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>, <xref:System.Xml.Linq.XText> , nebo je přidán jako podřízený obsah.  
  
- Je <xref:System.Collections.IEnumerable> výčtu a tato pravidla jsou použity rekurzivně na výsledky.  
  
- Pro jakýkoli jiný `ToString` typ je volána jeho metoda a výsledek je přidán jako textový obsah.  
  
### <a name="creating-an-xelement-with-content"></a>Vytvoření prvku XElement s obsahem  
 Můžete vytvořit, <xref:System.Xml.Linq.XElement> který obsahuje jednoduchý obsah s voláním jedné metody. Chcete-li to provést, zadejte obsah jako druhý parametr takto:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Jako obsah můžete předat libovolný typ objektu. Například následující kód vytvoří prvek, který obsahuje číslo s plovoucí desetinnou čárkou jako obsah:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Číslo s plovoucí desetinnou tácem je zabaleno a předáno konstruktoru. Zabalené číslo je převedeno na řetězec a použito jako obsah prvku.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Vytvoření prvku XElement s podřízeným prvkem  
 Pokud předáte instanci <xref:System.Xml.Linq.XElement> třídy pro argument obsahu, konstruktor vytvoří prvek s podřízeným elementem:  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Vytvoření prvku XElement s více podřízenými prvky  
 Můžete předat několik <xref:System.Xml.Linq.XElement> objektů pro obsah. Každý z <xref:System.Xml.Linq.XElement> objektů je součástí jako podřízený prvek.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Rozšířením výše uvedeného příkladu můžete vytvořit celý strom XML takto:  
  
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
Console.WriteLine(contacts);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  

### <a name="creating-an-xelement-with-an-xattribute"></a>Vytvoření prvku XElement s atributem X
 Pokud předáte instanci <xref:System.Xml.Linq.XAttribute> třídy pro argument obsahu, konstruktor vytvoří prvek s atributem:

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a>Vytvoření prázdného prvku  
 Chcete-li <xref:System.Xml.Linq.XElement>vytvořit prázdný , nepředáte žádný obsah konstruktoru. Následující příklad vytvoří prázdný prvek:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Připojení vs. klonování  
 Jak již bylo zmíněno <xref:System.Xml.Linq.XElement>dříve, <xref:System.Xml.Linq.XAttribute> při přidávání <xref:System.Xml.Linq.XNode> (včetně) nebo objektů, pokud nový obsah nemá nadřazený obsah, objekty jsou jednoduše připojeny ke stromu XML. Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, nový obsah je klonován a nově klonovaný obsah je připojen ke stromu XML.  

Následující příklad ukazuje chování při přidání nadřazeného prvku do stromu a při přidání prvku bez nadřazeného prvku do stromu.

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a>Viz také

- [Vytváření stromů XML (C#)](./linq-to-xml-overview.md)
