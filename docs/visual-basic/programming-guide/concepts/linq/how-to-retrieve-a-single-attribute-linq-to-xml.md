---
title: 'Postupy: načtení jednoho atributu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 02afbc987cf9f55d16bb56912f3eaf45cd8c9a37
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347567"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Postupy: načtení jednoho atributu (LINQ to XML) (Visual Basic)
Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu. To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.  
  
 Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement> vrací <xref:System.Xml.Linq.XAttribute> se zadaným názvem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá metodu <xref:System.Xml.Linq.XElement.Attribute%2A>.  
  
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
  
 Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone`a poté vyhledá atribut s názvem `type`.  
  
 Tento kód generuje následující výstup:  
  
```console  
home  
work  
```  
  
## <a name="example"></a>Příklad  
 Pokud chcete načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u objektů <xref:System.Xml.Linq.XElement>. Následující příklad ukazuje to.  
  
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
  
 Tento kód generuje následující výstup:  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje explicitní operátory přetypování pro třídu <xref:System.Xml.Linq.XAttribute> na `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID``GUID?`  
  
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
  
 Tento kód generuje následující výstup:  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
