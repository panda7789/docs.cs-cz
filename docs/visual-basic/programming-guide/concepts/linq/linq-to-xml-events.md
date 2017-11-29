---
title: "Technologie LINQ to XML události (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19d8f19f9feb1d385f9900d76d2a7af8e89bbeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-events-visual-basic"></a>Technologie LINQ to XML události (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]události umožňují být upozorněni, když je změnit strom XML.  
  
 Události můžete přidat do instance libovolného <xref:System.Xml.Linq.XObject>. Obslužné rutiny události bude potom přijímat události pro změny, <xref:System.Xml.Linq.XObject> a všechny jeho podřízené položky. Můžete například přidat obslužné rutiny události ke kořenu stromu a zpracovat všechny změny do stromu z této obslužné rutiny události.  
  
 Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] události, viz <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Typy a události  
 Při práci s událostmi se používají následující typy:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.|  
  
 Při úpravě strom XML, jsou vyvolány následující události:  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Dojde k těsně před <xref:System.Xml.Linq.XObject> nebo některý z jeho následníky se chystáte změnit.|  
|<xref:System.Xml.Linq.XObject.Changed>|Nastane při <xref:System.Xml.Linq.XObject> došlo ke změně nebo některé z jejich potomků změnily.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Události jsou užitečné, pokud chcete zachovat některé agregační informace ve stromu XML. Například můžete udržovat celkovou fakturu představuje součet položek řádku faktury. Tento příklad používá událostí udržovat celkový počet všech podřízených elementů v části komplexních prvků `Items`.  
  
### <a name="code"></a>Kód  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentáře  
 Tento kód vytvoří následující výstup:  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé technologie LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
