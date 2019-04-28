---
title: 'Postupy: Stream fragmentů XML pomocí přístup k informacím hlavičky (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: c11a64eb28e8952636ab877479852bd883fc7eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614644"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Postupy: Stream fragmentů XML pomocí přístup k informacím hlavičky (Visual Basic)
Někdy je nutné číst libovolně velké soubory XML a zapisovat vaše aplikace tak, aby nároky na paměť pro aplikace předvídatelné. Pokud se pokusíte k naplnění stromu XML pomocí velkého souboru XML, využití paměti bude přímo úměrná velikosti souboru – to znamená, nadměrné. Proto měli používat streamování technika místo.  
  
 Jednou z možností je pro zápis aplikace pomocí <xref:System.Xml.XmlReader>. Však můžete chtít použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz stromu XML. Pokud je to tento případ, můžete napsat vlastní metodu vlastní osy. Další informace najdete v tématu [jak: Zápis metody osy XML (Visual Basic) LINQ](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Chcete-li napsat vlastní metodu osy, napište malé metody, která používá <xref:System.Xml.XmlReader> číst uzly, dokud nebude dosaženo jednoho z uzlů, které vás zajímají. Pak zavolá metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A>, která čte z <xref:System.Xml.XmlReader> a vytvoří instanci XML fragment. Můžete pak zápis dotazů LINQ na vaše vlastní osy metoda.  
  
 Streamování techniky aplikují nejlépe v situacích, kde je potřeba zpracovat zdrojový dokument pouze jednou a může zpracovat prvky v pořadí dokumentů. Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iterovat jejich zdroj, shromáždit všechna data, seřadit a nakonec yield první položky v sekvenci. Všimněte si, že pokud použijete operátor dotazu, který bude realizována zdrojem před získávání první položka, nebude zachovat malé paměťové nároky.  
  
## <a name="example"></a>Příklad  
 Někdy problém získá jen málo další zajímavé. V následujícím dokumentu XML příjemce vaše vlastní osy metoda má také znát název zákazníka, který jednotlivé položky patří do.  
  
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
  
 Přístup, který přijímá v tomto příkladu je taky sledovat informace hlavičky, uložit informace v záhlaví a následně vytvořit malé stromu XML, který obsahuje informace v záhlaví a podrobností, které jsou výčet. Metoda osy poskytuje pak tento nový, malé stromu XML. Dotaz potom má přístup k informace hlavičky, jakož i podrobné informace.  
  
 Tento přístup má malé paměťové nároky. Každý detail fragment XML, je vhodné, žádné odkazy jsou omezeny na předchozí fragment, a je k dispozici pro uvolnění paměti. Všimněte si, že tento postup vytvoří mnoho krátkodobý objektů na haldě.  
  
 Následující příklad ukazuje, jak implementovat a používat vlastní osy metodu, která jsou streamována fragmentů XML ze souboru určeného identifikátorem URI. Tato vlastní osy je vytvořených speciálně tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` elementy a, tyto prvky se uspořádané jako výše `Source.xml` dokumentu. Je zjednodušenou implementaci. Robustnější implementace by být připraveni analyzovat neplatný dokument.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Pokročilé technologie LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
