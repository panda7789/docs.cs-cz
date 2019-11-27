---
title: 'Postupy: streamování fragmentů XML s přístupem k informacím záhlaví'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 489e128e86a47e0e7f76c14a6cf1baf80fb0c406
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332454"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a>Postupy: streamování fragmentů XML s přístupem k informacím hlavičky (Visual Basic)
Někdy je nutné číst libovolně velké soubory XML a napsat aplikaci tak, aby paměti aplikace byly předvídatelné. Pokud se pokusíte naplnit strom XML velkým souborem XML, využití paměti bude úměrné velikosti souboru, tedy nadměrné. Proto byste měli místo toho použít metodu streamování.  
  
 Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader>. Je však vhodné použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k dotazování stromu XML. Pokud se jedná o tento případ, můžete napsat vlastní metodu osy. Další informace naleznete v tématu [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Chcete-li napsat vlastní metodu osy, napíšete malou metodu, která používá <xref:System.Xml.XmlReader> ke čtení uzlů, dokud nedosáhne jednoho z uzlů, které vás zajímají. Metoda pak zavolá <xref:System.Xml.Linq.XNode.ReadFrom%2A>, které čtou z <xref:System.Xml.XmlReader> a vytvoří instanci fragmentu XML. Pak můžete napsat dotazy LINQ na vlastní metodu osy.  
  
 Techniky streamování se nejlépe aplikují v situacích, kdy potřebujete zpracovat zdrojový dokument jenom jednou, a můžete zpracovat elementy v pořadí dokumentů. Některé standardní operátory pro dotazování, jako je například <xref:System.Linq.Enumerable.OrderBy%2A>, iterují jejich zdroj, shromažďují všechna data, řadí je a nakonec vydávají první položku v sekvenci. Všimněte si, že pokud použijete operátor dotazu, který materializuje svůj zdroj před tím, než zadáte první položku, nebudete si uchovávat malý objem paměti.  
  
## <a name="example"></a>Příklad  
 Někdy je problém jenom trochu zajímavější. V následujícím dokumentu XML musí příjemce vlastní metody osy také znát název zákazníka, ke kterému každá položka patří.  
  
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
  
 Přístup v tomto příkladu je také sledován pro tyto informace hlavičky, uložení informací v hlavičce a následné sestavení malého stromu XML, který obsahuje jak informace v hlavičce, tak i podrobnosti, které provádíte ve výčtu. Metoda Axis pak tento nový malý strom XML. Dotaz pak má přístup k informacím v hlavičce a také k podrobným informacím.  
  
 Tento přístup má malé nároky na paměť. Vzhledem k tomu, že se přestanou fragmenty XML, nezachovají se žádné odkazy na předchozí fragment a je k dispozici pro uvolňování paměti. Všimněte si, že tato technika vytváří mnoho krátkodobých objektů v haldě.  
  
 Následující příklad ukazuje, jak implementovat a použít vlastní metodu osy, která streamuje fragmenty XML ze souboru určeného identifikátorem URI. Tato vlastní osa je určena konkrétně tak, že očekává dokument, který má `Customer`, `Name`a `Item` prvky a že tyto prvky budou uspořádány jako v předchozím `Source.xml` dokumentu. Jedná se o zjednodušený implementaci. Robustnější implementace by se připravila k analýze neplatného dokumentu.  
  
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
  
 Tento kód generuje následující výstup:  
  
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

- [Rozšířené programování LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
