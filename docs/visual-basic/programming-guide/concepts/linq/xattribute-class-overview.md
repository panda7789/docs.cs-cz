---
title: Přehled třídy XAttribute (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 08b8ebf31a39325c98023d4bb333f8e06bbdeb3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406425"
---
# <a name="xattribute-class-overview-visual-basic"></a>Přehled třídy XAttribute (Visual Basic)
Atributy jsou páry název/hodnota, které jsou spojeny s elementem. <xref:System.Xml.Linq.XAttribute> Třída reprezentuje atributy ve formátu XML.  
  
## <a name="overview"></a>Přehled  
 Práce s atributy v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je podobně jako při práci s prvky. Jejich konstruktory jsou podobné. Metody, které můžete použít k načtení kolekce z nich jsou podobné. A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu dotazu pro kolekci atributů vypadá podobně jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu pro kolekci elementů dotazu.  
  
 Zachování pořadí, ve kterém byly přidány atributy pro element. To znamená když iteraci atributy, uvidíte je ve stejném pořadí, v jakém byly přidány.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Následující konstruktor třídy <xref:System.Xml.Linq.XAttribute> třída je ten, který budete používat nejčastěji:  
  
|Konstruktor|Popis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Vytvoří <xref:System.Xml.Linq.XAttribute> objektu. `name` Argument určuje název atributu. `content` určuje obsah atributu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Vytvoření elementu s atributem  
 Následující kód ukazuje element, který obsahuje atribut pomocí literálů XML v jazyce Visual Basic:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Funkční konstrukce atributů  
 Můžete vytvořit <xref:System.Xml.Linq.XAttribute> objekty v řádku s konstrukci <xref:System.Xml.Linq.XElement> objekty, následujícím způsobem:  
  
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
  
### <a name="attributes-are-not-nodes"></a>Atributy nejsou uzly  
 Existuje několik rozdílů mezi elementy a atributy. <xref:System.Xml.Linq.XAttribute> objekty nejsou uzlů ve stromové struktuře XML. Jsou páry název/hodnota přidružený platný element XML. Na rozdíl od Document Object Model (DOM), to lépe odpovídá struktuře XML. I když <xref:System.Xml.Linq.XAttribute> objekty nejsou ve skutečnosti uzlů ve stromu XML, práce s <xref:System.Xml.Linq.XAttribute> je velmi podobně jako při práci s objekty <xref:System.Xml.Linq.XElement> objekty.  
  
 Tento rozdíl je důležité především pouze pro vývojáře, kteří jsou psaní kódu, který funguje s stromů XML na úrovni uzlu. Mnoho vývojářů nesmí být obeznámeni s toto rozlišení.  
  
## <a name="see-also"></a>Viz také  
 [Přehled LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
