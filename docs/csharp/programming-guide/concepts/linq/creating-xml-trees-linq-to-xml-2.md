---
title: Vytváření stromů XML v jazyce C# (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4fcd0c14970dd4aabe4d51335f9a0a0a991ef019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335459"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Vytváření stromů XML v jazyce C# (LINQ to XML)
Tato část obsahuje informace o vytváření stromů XML v jazyce C#.  
  
 Informace o používání výsledky dotazů LINQ jako obsah pro <xref:System.Xml.Linq.XElement>, najdete v části [funkční konstrukce (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Vytváření elementů  
 Signatur <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňují předat obsah elementu nebo atributu jako argumenty pro konstruktor. Protože jeden z konstruktorů přijímá proměnný počet argumentů, které lze předat libovolný počet podřízených prvků. Samozřejmě každý z těchto podřízených elementů může obsahovat vlastní podřízené elementy. Pro libovolný element můžete přidat libovolný počet atributů.  
  
 Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud se nový obsah nemá nadřazený, jsou objekty jednoduše připojené k stromové struktuře XML. Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonována nový obsah a nově naklonovaný obsah je připojen k stromové struktuře XML. Poslední příklad v tomto tématu ukazuje to.  
  
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
  
 Pokud odsazeny správně, kód k vytvoření <xref:System.Xml.Linq.XElement> objekty velmi podobá strukturu základní XML.  
  
## <a name="xelement-constructors"></a>XElement konstruktory  
 <xref:System.Xml.Linq.XElement> Třída používá těchto konstruktorů pro tvorbu funkční. Všimněte si, že jsou některé konstruktory pro <xref:System.Xml.Linq.XElement>, ale vzhledem k tomu, že se nepoužívají pro funkční konstrukce zde nejsou uvedeny.  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Vytvoří <xref:System.Xml.Linq.XElement>. `name` Parametr určuje název elementu; `content` určuje obsah elementu.|  
|`XElement(XName name)`|Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializována tak, aby zadaný název.|  
|`XElement(XName name, params object[] content)`|Vytvoří <xref:System.Xml.Linq.XElement> s jeho <xref:System.Xml.Linq.XName> inicializována tak, aby zadaný název. Atributy nebo podřízené elementy jsou vytvořené pomocí obsah seznam parametrů.|  
  
 `content` Parametr je velmi flexibilní. Podporuje jakéhokoli typu objektu, který je platný podřízeným <xref:System.Xml.Linq.XElement>. Pro různé typy objektů předán v tomto parametru platí následující pravidla:  
  
-   Řetězec se přidá jako textového obsahu.  
  
-   <xref:System.Xml.Linq.XElement> Je přidána jako podřízený element.  
  
-   <xref:System.Xml.Linq.XAttribute> Se přidá jako atribut.  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, Nebo <xref:System.Xml.Linq.XText> je přidána jako podřízený obsah.  
  
-   <xref:System.Collections.IEnumerable> Je výčet, a tato pravidla jsou použita rekurzivně výsledky.  
  
-   U ostatních typů jeho `ToString` metoda je volána a výsledek je přidána jako textového obsahu.  
  
### <a name="creating-an-xelement-with-content"></a>Vytvoření XElement s obsahem  
 Můžete vytvořit <xref:System.Xml.Linq.XElement> obsahující jednoduchý obsah pomocí volání jedné metody. K tomuto účelu určete obsah jako druhý parametr následujícím způsobem:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Jako obsah můžete předat libovolný typ objektu. Například následující kód vytvoří elementu, který obsahuje plovoucí bodu číslo jako obsah:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Plovoucí bod je číslo do pole a v předaný konstruktoru. Pevně určené číslo je převedeno na řetězec a použít jako obsah elementu.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Vytvoření XElement s podřízený Element  
 Pokud předáte instanci <xref:System.Xml.Linq.XElement> třída obsahu argument konstruktoru vytvoří element s podřízený element:  
  
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
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Vytvoření XElement s více podřízených elementů  
 Můžete předat za počet <xref:System.Xml.Linq.XElement> objekty pro obsah. Každý z <xref:System.Xml.Linq.XElement> objekty se dodává jako podřízený element.  
  
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
  
 Tím, že rozšíří výše uvedeném příkladu, můžete vytvořit celý strom XML, následujícím způsobem:  
  
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
  
### <a name="creating-an-empty-element"></a>Vytvoření prázdného prvku  
 Chcete-li vytvořit prázdnou <xref:System.Xml.Linq.XElement>, můžete do konstruktoru nepředávejte žádný obsah. Následující příklad vytvoří prázdný element:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Připojení vs. Klonování  
 Jak je uvedeno nahoře, při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud se nový obsah nemá nadřazený, jsou objekty jednoduše připojené k stromové struktuře XML. Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, naklonována nový obsah a nově naklonovaný obsah je připojen k stromové struktuře XML.  
  
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
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
