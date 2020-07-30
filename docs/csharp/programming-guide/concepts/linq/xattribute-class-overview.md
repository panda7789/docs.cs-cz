---
title: XAttribute – Přehled třídy (C#)
description: Atributy jsou páry název-hodnota přidružené k elementu. XAttribute představuje atributy XML. Přečtěte si o práci s atributy v LINQ to XML v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 8a19de601041bbb20241c959e909483b97bcf797
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302227"
---
# <a name="xattribute-class-overview-c"></a>XAttribute – Přehled třídy (C#)
Atributy jsou páry název-hodnota, které jsou přidruženy k elementu. <xref:System.Xml.Linq.XAttribute>Třída představuje atributy XML.  
  
## <a name="overview"></a>Přehled  
 Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s prvky. Jejich konstruktory jsou podobné. Metody, které použijete k načtení kolekcí, jsou podobné. Výraz dotazu LINQ pro kolekci atributů vypadá velmi podobně jako výraz dotazu LINQ pro kolekci prvků.  
  
 Pořadí, ve kterém byly přidány atributy do prvku, je zachováno. To znamená, že při iteraci pomocí atributů se zobrazí ve stejném pořadí, v jakém byly přidány.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Následující konstruktor <xref:System.Xml.Linq.XAttribute> třídy je ten, který se nejčastěji používá:  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Vytvoří objekt <xref:System.Xml.Linq.XAttribute>. `name`Argument určuje název atributu; `content` určuje obsah atributu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Vytvoření elementu s atributem  
 Následující kód ukazuje běžný úkol při vytváření prvku, který obsahuje atribut:  
  
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
  
### <a name="functional-construction-of-attributes"></a>Funkční konstrukce atributů  
 Objekty lze vytvořit <xref:System.Xml.Linq.XAttribute> v řádku pomocí konstrukce <xref:System.Xml.Linq.XElement> objektů, a to následujícím způsobem:  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
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
  
### <a name="attributes-are-not-nodes"></a>Atributy nejsou uzly.  
 Mezi atributy a elementy existují rozdíly. <xref:System.Xml.Linq.XAttribute>objekty nejsou uzly ve stromu XML. Jsou to páry název-hodnota přidružené k elementu XML. Na rozdíl od model DOM (Document Object Model) (DOM) to přesněji odráží strukturu XML. Přestože <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzly ve stromu XML, práce s <xref:System.Xml.Linq.XAttribute> objekty je velmi podobná práci s <xref:System.Xml.Linq.XElement> objekty.  
  
 Toto rozlišení je primárně důležité pouze pro vývojáře, kteří píší kód, který pracuje s stromy XML na úrovni uzlu. Toto rozlišení se netýká mnoha vývojářů.  
  
## <a name="see-also"></a>Viz také:

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)
