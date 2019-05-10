---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 00f528bca00b2c2316d949ceb3b6c4bba2499146
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597665"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Vytváření stromů XML v jazyce C# (LINQ to XML)
Tato část obsahuje informace o vytváření stromů XML v jazyce C#.  
  
 Další informace o použití výsledků dotazů LINQ jako obsah pro <xref:System.Xml.Linq.XElement>, naleznete v tématu [funkční konstrukce (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Vytváření elementů
 Podpisy <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňují obsah elementu nebo atributu předat jako argumenty konstruktoru. Protože jeden z konstruktorů přebírá proměnný počet argumentů, můžete předat libovolný počet podřízených elementů. Samozřejmě každá z těchto podřízených elementů může obsahovat vlastní podřízené prvky. Pro libovolný element můžete přidat libovolný počet atributů.  
  
 Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud se nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojené do stromu XML. Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonované nový obsah a nově naklonovaného obsahu je připojen ke stromu XML. V poslední příkladu v tomto tématu ukazuje to.  
  
 Chcete-li vytvořit `contacts` <xref:System.Xml.Linq.XElement>, můžete použít následující kód:  
  
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
  
 Pokud odsazena správně, kód k vytvoření <xref:System.Xml.Linq.XElement> objekty podobá struktuře základní XML.  
  
## <a name="xelement-constructors"></a>Konstruktory XElement  
 <xref:System.Xml.Linq.XElement> Třída používá následující konstruktory pro funkční konstrukce. Všimněte si, že jsou některé konstruktory pro <xref:System.Xml.Linq.XElement>, ale vzhledem k tomu, že nejsou použity pro funkční konstrukce, které zde nejsou uvedeny.  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Vytvoří <xref:System.Xml.Linq.XElement>. `name` Parametr určuje název elementu; `content` určuje obsah elementu.|  
|`XElement(XName name)`|Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializovány na zadaný název.|  
|`XElement(XName name, params object[] content)`|Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializovány na zadaný název. Atributy a podřízené prvky jsou vytvořeny z obsahu seznamu parametrů.|  
  
 `content` Parametr je velmi flexibilní. Podporuje jakýkoli typ objektu, který je platný podřízený <xref:System.Xml.Linq.XElement>. Následující pravidla platí pro různé druhy objektů předaných v tomto parametru:  
  
- Řetězec se přidá jako textový obsah.  
  
- <xref:System.Xml.Linq.XElement> Je přidán jako podřízený element.  
  
- <xref:System.Xml.Linq.XAttribute> Se přidá jako atribut.  
  
- <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, Nebo <xref:System.Xml.Linq.XText> je přidán jako podřízený obsah.  
  
- <xref:System.Collections.IEnumerable> Výčtu a tato pravidla jsou aplikována rekurzivně na výsledky.  
  
- Pro jakýkoli jiný typ jeho `ToString` volání metody a výsledek se přidá jako textový obsah.  
  
### <a name="creating-an-xelement-with-content"></a>Vytváření s obsahem na XElement  
 Můžete vytvořit <xref:System.Xml.Linq.XElement> , který obsahuje jednoduchý obsah pomocí jedné metody volání. Chcete-li to provést, určení obsahu jako druhý parametr následujícím způsobem:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Libovolný typ objektu lze předat jako obsah. Například následující kód vytvoří element, který obsahuje plovoucí číslo jako obsah bodu:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Plovoucí desetinná čárka je číslo v poli a předaná do konstruktoru. Pevně určené číslo je převedeno na řetězec a použít jako obsah elementu.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Vytváření s podřízeným elementem na XElement  
 Pokud předáte instanci <xref:System.Xml.Linq.XElement> třídy obsahu argument konstruktoru vytvoří element s podřízený element:  
  
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
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Vytváření XElement s více podřízených prvků  
 Můžete předat několik <xref:System.Xml.Linq.XElement> objekty pro obsah. Každá z <xref:System.Xml.Linq.XElement> objekty je dostupná jako podřízený element.  
  
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
  
 Tím, že rozšíří výše uvedeném příkladu, můžete vytvořit celý strom XML následujícím způsobem:  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a>Vytvoření pomocí XAttribute XElement
 Pokud předáte instanci <xref:System.Xml.Linq.XAttribute> třídy obsahu argument konstruktoru vytvoří element se atribut:

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

### <a name="creating-an-empty-element"></a>Vytvořit prázdný element  
 Chcete-li vytvořit prázdnou <xref:System.Xml.Linq.XElement>, konstruktoru nepředáte žádný obsah. Následující příklad vytvoří prázdný element:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Připojení a klonování  
 Jak už bylo zmíněno dříve, při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud se nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojené do stromu XML. Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonované nový obsah a nově naklonovaného obsahu je připojen ke stromu XML.  

Následující příklad ukazuje chování při přidávání nadřazeným prvkem elementu do stromu a přidejte element s žádný nadřazený objekt na strom.

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

- [Vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
