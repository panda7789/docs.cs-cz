---
title: Přehled třídy XAttribute (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635662"
---
# <a name="xattribute-class-overview-c"></a>Přehled třídy XAttribute (C#)
Atributy jsou dvojice název/hodnota, které jsou přidruženy k prvku. Třída <xref:System.Xml.Linq.XAttribute> představuje atributy XML.  
  
## <a name="overview"></a>Přehled  
 Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s prvky. Jejich konstruktéři jsou si podobní. Metody, které používáte k načtení kolekce z nich jsou podobné. Výraz dotazu LINQ pro kolekci atributů vypadá velmi podobně jako výraz dotazu LINQ pro kolekci prvků.  
  
 Pořadí, ve kterém byly přidány atributy do prvku, je zachováno. To znamená, že když itetujete atributy, zobrazí se ve stejném pořadí, v jakém byly přidány.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Následující konstruktor třídy <xref:System.Xml.Linq.XAttribute> je ten, který budete nejčastěji používat:  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Vytvoří objekt <xref:System.Xml.Linq.XAttribute>. Argument `name` určuje název atributu; `content` určuje obsah atributu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Vytvoření prvku s atributem  
 Následující kód ukazuje společný úkol vytvoření prvku, který obsahuje atribut:  
  
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
  
### <a name="functional-construction-of-attributes"></a>Funkční konstrukce atributů  
 Objekty <xref:System.Xml.Linq.XAttribute> můžete vytvořit v souladu <xref:System.Xml.Linq.XElement> s konstrukcí objektů takto:  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>Atributy nejsou uzly  
 Existují určité rozdíly mezi atributy a prvky. <xref:System.Xml.Linq.XAttribute>objekty nejsou uzly ve stromu XML. Jedná se o dvojice název/hodnota přidružené k elementu XML. Na rozdíl od modelu Document Object Model (DOM) to lépe odráží strukturu jazyka XML. Přestože <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzly ve stromu XML, práce s <xref:System.Xml.Linq.XAttribute> objekty je velmi podobná práci s <xref:System.Xml.Linq.XElement> objekty.  
  
 Toto rozlišení je důležité především pro vývojáře, kteří píší kód, který pracuje se stromy XML na úrovni uzlu. Mnoho vývojářů se tímto rozdílem nebude zabývat.  
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)
