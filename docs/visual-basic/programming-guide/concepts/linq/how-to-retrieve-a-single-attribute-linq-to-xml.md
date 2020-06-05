---
title: 'Postupy: Načtení jednoho atributu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 34c390fbffc1aea68a2fd8ae64b17d2637a1f4f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397853"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Postupy: načtení jednoho atributu (LINQ to XML) (Visual Basic)
Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu. To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.  
  
 <xref:System.Xml.Linq.XElement.Attribute%2A>Metoda <xref:System.Xml.Linq.XElement> třídy vrací se <xref:System.Xml.Linq.XAttribute> zadaným názvem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Xml.Linq.XElement.Attribute%2A> metodu.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone` a pak vyhledá atribut s názvem `type` .  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
home  
work  
```  
  
## <a name="example"></a>Příklad  
 Chcete-li načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u s <xref:System.Xml.Linq.XElement> objekty. Následující příklad ukazuje to.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje explicitní operátory přetypování pro <xref:System.Xml.Linq.XAttribute> třídu na `string` , `bool` ,,, `bool?` `int` `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,, a.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ to XML osy (Visual Basic)](linq-to-xml-axes.md)
