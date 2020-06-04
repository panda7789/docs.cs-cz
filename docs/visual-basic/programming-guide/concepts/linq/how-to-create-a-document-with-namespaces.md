---
title: 'Postupy: Vytvoření dokumentu pomocí názvových prostorů (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: a440c9d810798eb5ebd025a336cbb17fface23b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414631"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Postupy: vytvoření dokumentu s oborem názvů (LINQ to XML) (Visual Basic)
V tomto tématu se dozvíte, jak vytvořit dokument s obory názvů v Visual Basic.  
  
 Při použití literálů XML v Visual Basic mohou uživatelé definovat jeden globální výchozí obor názvů XML. Tento obor názvů je výchozím oborem názvů pro literály XML a vlastnosti XML. Výchozí obor názvů XML lze definovat buď na úrovni projektu, nebo na úrovni souboru. Pokud je definována na úrovni souboru, přepisuje výchozí obor názvů na úrovni projektu.  
  
 Můžete také definovat jiné obory názvů a zadat předpony oboru názvů pro tyto obory názvů.  
  
 Můžete definovat výchozí obory názvů a obory názvů s předponou pomocí `Imports` klíčového slova.  
  
 Další informace naleznete v tématu [Úvod do literálů XML v Visual Basic](introduction-to-xml-literals.md).  
  
 Všimněte si, že výchozí obor názvů XML se vztahuje pouze na elementy a nikoli na atributy. Atributy jsou ve výchozím nastavení vždy v žádném oboru názvů. Můžete však použít předponu oboru názvů pro vložení atributu do oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří dokument, který obsahuje obor názvů.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří dokument, který obsahuje dva obory názvů, z nichž jeden je výchozím oborem názvů.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument, který obsahuje více oborů názvů, s předponami oboru názvů.  
  
 Při serializaci stromu XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vygeneruje deklarace oboru názvů podle potřeby, aby byl každý element v jeho určeném oboru názvů.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Viz také

- [Přehled oborů názvů (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
