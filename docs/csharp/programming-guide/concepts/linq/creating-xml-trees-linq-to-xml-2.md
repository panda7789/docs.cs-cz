---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: a77171ebbc07e54f6988fb97aff197b4c6d31721
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594623"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Vytváření stromů XML v C# (LINQ to XML)
Tato část poskytuje informace o vytváření stromů XML v C#nástroji.  
  
 Informace o použití výsledků dotazů LINQ jako obsahu pro <xref:System.Xml.Linq.XElement>naleznete v tématu [funkční konstrukce (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Vytváření elementů
 Signatury <xref:System.Xml.Linq.XElement> konstruktorů a <xref:System.Xml.Linq.XAttribute> umožňují předat obsah elementu nebo atributu jako argumenty konstruktoru. Vzhledem k tomu, že jeden z konstruktorů přebírá proměnný počet argumentů, můžete předat libovolný počet podřízených elementů. Každý z těchto podřízených elementů samozřejmě může obsahovat vlastní podřízené prvky. Pro libovolný prvek můžete přidat libovolný počet atributů.  
  
 Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud nový obsah nemá žádný nadřazený objekt, jsou objekty jednoduše připojeny ke stromu XML. Pokud nový obsah již je nadřazený a je součástí jiného stromu XML, bude nový obsah naklonován a nově Klonovaný obsah je připojen ke stromu XML. Příklad ukazuje poslední příklad v tomto tématu.  
  
 Chcete-li `contacts`vytvořit <xref:System.Xml.Linq.XElement>, můžete použít následující kód:  
  
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
  
 Pokud je znak správně odsazený, kód pro <xref:System.Xml.Linq.XElement> sestavování objektů se těsně podobá struktuře podkladového XML.  
  
## <a name="xelement-constructors"></a>XElement konstruktory  
 <xref:System.Xml.Linq.XElement> Třída používá následující konstruktory pro konstrukci funkčnosti. Všimněte si, že existují další konstruktory pro <xref:System.Xml.Linq.XElement>, ale vzhledem k tomu, že nejsou používány pro funkční konstrukce, nejsou zde uvedeny.  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<xref:System.Xml.Linq.XElement>Vytvoří. `name` Parametr určuje název elementu. `content` určuje obsah elementu.|  
|`XElement(XName name)`|<xref:System.Xml.Linq.XElement> Vytvoří snázvem,kterýjeinicializován<xref:System.Xml.Linq.XName> na zadaný název.|  
|`XElement(XName name, params object[] content)`|<xref:System.Xml.Linq.XElement> Vytvoří snázvem,kterýjeinicializován<xref:System.Xml.Linq.XName> na zadaný název. Atributy nebo podřízené prvky jsou vytvořeny z obsahu seznamu parametrů.|  
  
 `content` Parametr je velice flexibilní. Podporuje jakýkoliv typ objektu, který je platným podřízeným <xref:System.Xml.Linq.XElement>prvku. Následující pravidla platí pro různé typy objektů předaných v tomto parametru:  
  
- Řetězec se přidá jako textový obsah.  
  
- <xref:System.Xml.Linq.XElement> Je přidán jako podřízený element.  
  
- Přidá <xref:System.Xml.Linq.XAttribute> se jako atribut.  
  
- <xref:System.Xml.Linq.XProcessingInstruction>, Nebose<xref:System.Xml.Linq.XText> přidá jako podřízený obsah. <xref:System.Xml.Linq.XComment>  
  
- Vytvoří <xref:System.Collections.IEnumerable> se výčet a tato pravidla se rekurzivně aplikují na výsledky.  
  
- Pro jakýkoliv jiný typ je jeho `ToString` metoda volána a výsledek je přidán jako textový obsah.  
  
### <a name="creating-an-xelement-with-content"></a>Vytvoření XElement s obsahem  
 Můžete vytvořit <xref:System.Xml.Linq.XElement> , který obsahuje jednoduchý obsah s jedinou voláním metody. Chcete-li to provést, zadejte jako druhý parametr obsah následujícím způsobem:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Jako obsah můžete předat libovolný typ objektu. Například následující kód vytvoří prvek, který obsahuje číslo s plovoucí desetinnou čárkou jako obsah:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Číslo s plovoucí desetinnou čárkou je v krabici a předáno do konstruktoru. Zabalené číslo je převedeno na řetězec a použito jako obsah elementu.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Vytvoření XElement s podřízeným elementem  
 Pokud předáte instanci <xref:System.Xml.Linq.XElement> třídy pro argument obsahu, konstruktor vytvoří prvek s podřízeným elementem:  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Vytvoření XElement s více podřízenými elementy  
 Pro obsah můžete předat několik <xref:System.Xml.Linq.XElement> objektů. <xref:System.Xml.Linq.XElement> Každý objekt je zahrnut jako podřízený element.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Rozšířením výše uvedeného příkladu můžete vytvořit celý strom XML následujícím způsobem:  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a>Vytvoření XElement pomocí XAttribute
 Pokud předáte instanci <xref:System.Xml.Linq.XAttribute> třídy pro argument obsahu, konstruktor vytvoří element s atributem:

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```   

### <a name="creating-an-empty-element"></a>Vytvoření prázdného prvku  
 Chcete-li vytvořit <xref:System.Xml.Linq.XElement>prázdnou, nemusíte do konstruktoru předávat žádný obsah. Následující příklad vytvoří prázdný element:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Připojení vs. klonování  
 Jak bylo uvedeno dříve, při <xref:System.Xml.Linq.XNode> přidávání ( <xref:System.Xml.Linq.XElement>včetně) <xref:System.Xml.Linq.XAttribute> nebo objektů, pokud nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojeny ke stromu XML. Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, bude nový obsah klonován a nově Klonovaný obsah je připojen ke stromu XML.  

Následující příklad ukazuje chování při přidání nadřazeného elementu do stromu a při přidání elementu bez nadřazeného prvku do stromu.

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

## <a name="see-also"></a>Viz také:

- [Vytváření stromů XML (C#)](./linq-to-xml-overview.md)
