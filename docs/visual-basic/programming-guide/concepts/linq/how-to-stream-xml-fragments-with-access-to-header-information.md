---
title: 'Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 60ec63c33d20fa38bed32d9c46c4acfe649ecd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (Visual Basic)
Někdy je nutné ke čtení libovolně velké soubory XML a zapisovat vaše aplikace tak, aby nároky na paměť pro aplikace je předvídatelný. Pokud se pokusíte strom XML naplnění velký soubor XML, bude vaše využití paměti velikosti souboru – to znamená, nadměrné. Proto byste měli místo toho používat streamování techniku.  
  
 Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader>. Ale můžete chtít použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k dotazování stromové struktuře XML. Pokud je to tento případ, můžete napsat vlastní metodu vlastní osy. Další informace najdete v tématu [postupy: zápis LINQ metodě osy XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Zápis způsob osy, zápis malých metody, která používá <xref:System.Xml.XmlReader> číst uzlů, dokud nebude dosaženo jednoho z uzlů, které vás zajímá. Pak zavolá metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A>, který čte z <xref:System.Xml.XmlReader> a vytvoří XML fragment. Poté můžete napsat dotazů LINQ na metodu vlastní osy.  
  
 Streamování techniky nejlépe použity v situacích, kdy je potřeba zpracovat zdrojový dokument jenom jednou a může zpracovat elementy v pořadí dokumentů. Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iteraci zdrojových, shromáždit všechna data, řazení ji a nakonec yield první položky v sekvenci. Všimněte si, pokud používáte operátor dotazu, který bude realizována zdrojem před je první položka, nebude zachovali malou paměťovou zátěž.  
  
## <a name="example"></a>Příklad  
 Někdy problém získá jen málo další zajímavé. V následujícím dokumentu XML má příjemce metodu vlastní osy také znát název zákazníka, které patří každou položku.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 Přístup, který má v tomto příkladu je také sledovat informace hlavičky, uložit informace ze záhlaví a následně vytvořit malé stromu XML, který obsahuje informace v záhlaví a podrobností, která jsou vytváření výčtu. Metoda osy poskytuje pak tento nový, malé strom XML. Dotaz pak má přístup k informace hlavičky, jakož i podrobné informace.  
  
 Tento přístup má malou paměťovou zátěž. Každý fragment XML podrobností, je vhodné, jsou uchovány žádné odkazy na předchozí fragment, a je k dispozici pro uvolňování paměti. Všimněte si, že tento postup vytvoří mnoho zkrátí objektů v haldě.  
  
 Následující příklad ukazuje, jak implementovat a použít vlastní osy metodu, která datové proudy fragmenty XML ze souboru určeného identifikátor URI. Tato vlastní osy je speciálně tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` elementy a aby tyto prvky se být uspořádány jako výše `Source.xml` dokumentu. Je zneužívající vlastností prohlížeče implementace. Robustnější implementace by připravený k analýze neplatný dokument.  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim xmlTree = <Root>  
                          <%=  
                              From el In New StreamCustomerItem("Source.xml")  
                              Let itemKey = CInt(el.<Key>.Value)  
                              Where itemKey >= 3 AndAlso itemKey <= 7  
                              Select <Item>  
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>  
                                         <%= el.<Key> %>  
                                     </Item>  
                          %>  
                      </Root>  
  
        Console.WriteLine(xmlTree)  
    End Sub  
  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 Tento kód vytvoří následující výstup:  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé technologie LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
