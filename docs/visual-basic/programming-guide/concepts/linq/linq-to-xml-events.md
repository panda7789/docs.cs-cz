---
title: Události LINQ to XML
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368813"
---
# <a name="linq-to-xml-events-visual-basic"></a>Události LINQ to XML (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]události umožňují být upozorňovány při změně stromu XML.  
  
 Události můžete přidat do instance libovolné <xref:System.Xml.Linq.XObject> . Obslužná rutina události poté obdrží události pro úpravy tohoto <xref:System.Xml.Linq.XObject> a kteréhokoli z jeho potomků. Například můžete přidat obslužnou rutinu události do kořenového adresáře stromu a zpracovat všechny změny stromu z této obslužné rutiny události.  
  
 Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] událostí naleznete v tématech <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> .  
  
## <a name="types-and-events"></a>Typy a události  
 Při práci s událostmi můžete použít následující typy:  
  
|Typ|Description|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .|  
  
 Při úpravě stromu XML jsou vyvolány následující události:  
  
|Událost|Description|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Nastane těsně před tím, než <xref:System.Xml.Linq.XObject> se tato nebo kterákoli z jeho potomků změní.|  
|<xref:System.Xml.Linq.XObject.Changed>|Vyvolá se v případě, že došlo ke změně <xref:System.Xml.Linq.XObject> nebo některému z jeho potomků.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Description  
 Události jsou užitečné, pokud chcete zachovat některé agregované informace ve stromu XML. Například můžete chtít zachovat celkovou částku faktury, která je součtem položek řádků faktury. V tomto příkladu se používají události pro udržování celkového počtu všech podřízených elementů v rámci komplexního prvku `Items` .  
  
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
 Výsledkem tohoto kódu je následující výstup:  
  
```console  
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

- [Rozšířené programování LINQ to XML (Visual Basic)](advanced-linq-to-xml-programming.md)
