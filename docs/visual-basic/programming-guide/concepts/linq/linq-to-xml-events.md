---
title: Události LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: 5860a83c6475eb8cf150bb1c439bdd8499b6a2c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637794"
---
# <a name="linq-to-xml-events-visual-basic"></a>Události LINQ to XML (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] události umožňují upozorněni, když je změněna stromu XML.  
  
 Události můžete přidat do instance libovolného <xref:System.Xml.Linq.XObject>. Obslužná rutina události se pak zobrazí události pro změny, které <xref:System.Xml.Linq.XObject> a všech jejích potomků. Můžete například přidat obslužnou rutinu události pro kořen stromu a zpracovat všechny změny do stromové struktury z této obslužné rutiny události.  
  
 Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] události, viz <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Typy a události  
 Při práci s událostmi se používají následující typy:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.|  
  
 Při úpravě stromu XML jsou vyvolány následující události:  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Nastane bezprostředně před <xref:System.Xml.Linq.XObject> nebo libovolného z jeho potomků se to změnit.|  
|<xref:System.Xml.Linq.XObject.Changed>|Vyvolá se při <xref:System.Xml.Linq.XObject> došlo ke změně nebo libovolného z jeho potomků změnily.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Události jsou užitečné, pokud chcete zachovat některé agregované informace ve stromu XML. Například můžete udržovat celkovou fakturu, který je součtem řádku položek faktury. Tento příklad používá události k údržbě celkový součet všech podřízených elementů v rámci komplexních prvků `Items`.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Pokročilé technologie LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
