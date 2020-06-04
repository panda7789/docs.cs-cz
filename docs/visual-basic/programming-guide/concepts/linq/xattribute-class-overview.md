---
title: Přehled třídy XAttribute
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 5b165044b4bea83e1a0789e3dd00367ed27b43e8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413203"
---
# <a name="xattribute-class-overview-visual-basic"></a>Přehled třídy XAttribute (Visual Basic)
Atributy jsou páry název-hodnota, které jsou přidruženy k elementu. <xref:System.Xml.Linq.XAttribute>Třída představuje atributy XML.  
  
## <a name="overview"></a>Přehled  
 Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobná práci s prvky. Jejich konstruktory jsou podobné. Metody, které použijete k načtení kolekcí, jsou podobné. Výraz dotazu LINQ pro kolekci atributů vypadá velmi podobně jako výraz dotazu LINQ pro kolekci prvků.  
  
 Pořadí, ve kterém byly přidány atributy do prvku, je zachováno. To znamená, že při iteraci pomocí atributů se zobrazí ve stejném pořadí, v jakém byly přidány.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Následující konstruktor <xref:System.Xml.Linq.XAttribute> třídy je ten, který se nejčastěji používá:  
  
|Konstruktor|Description|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Vytvoří objekt <xref:System.Xml.Linq.XAttribute>. `name`Argument určuje název atributu; `content` určuje obsah atributu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Vytvoření elementu s atributem  
 Následující kód ukazuje prvek, který obsahuje atribut pomocí literálů XML v Visual Basic:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Funkční konstrukce atributů  
 Objekty lze vytvořit <xref:System.Xml.Linq.XAttribute> v řádku pomocí konstrukce <xref:System.Xml.Linq.XElement> objektů, a to následujícím způsobem:  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
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
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
