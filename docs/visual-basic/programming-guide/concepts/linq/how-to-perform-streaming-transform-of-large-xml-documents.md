---
title: 'Postup: Provedení transformace streamování velkých dokumentů XML'
ms.date: 07/20/2015
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
ms.openlocfilehash: f5e6063f0a850c03a605d75b0cbdc0bf9e03b325
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267012"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="87ea6-102">Postup: Provedení transformace streamování velkých dokumentů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87ea6-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="87ea6-103">Někdy budete muset transformovat velké soubory XML a zapsat aplikaci tak, aby nároky na paměť aplikace je předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="87ea6-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="87ea6-104">Pokud se pokusíte naplnit strom XML velmi velkým souborem XML, bude využití paměti úměrné velikosti souboru (to znamená nadměrné).</span><span class="sxs-lookup"><span data-stu-id="87ea6-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="87ea6-105">Proto byste měli místo toho použít techniku streamování.</span><span class="sxs-lookup"><span data-stu-id="87ea6-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="87ea6-106">Techniky streamování jsou nejvhodnější v situacích, kdy je třeba zpracovat zdrojový dokument pouze jednou a prvky můžete zpracovat v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="87ea6-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="87ea6-107">Některé standardní operátory <xref:System.Linq.Enumerable.OrderBy%2A>dotazů, například , iterate jejich zdroj, shromažďovat všechna data, seřadit a nakonec výnos první položku v pořadí.</span><span class="sxs-lookup"><span data-stu-id="87ea6-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="87ea6-108">Všimněte si, že pokud použijete operátor dotazu, který zhmotní jeho zdroj před získávání první položky, nezachováte malé nároky na paměť pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87ea6-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="87ea6-109">I v případě, že použijete techniku popsanou v [části Postup: Streamovat fragmenty XML s přístupem k informacím záhlaví (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), pokud se pokusíte sestavit strom XML, který obsahuje transformovaný dokument, využití paměti bude příliš velké.</span><span class="sxs-lookup"><span data-stu-id="87ea6-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="87ea6-110">Existují dva hlavní přístupy.</span><span class="sxs-lookup"><span data-stu-id="87ea6-110">There are two main approaches.</span></span> <span data-ttu-id="87ea6-111">Jedním z přístupů je použití <xref:System.Xml.Linq.XStreamingElement>odložených vlastností zpracování .</span><span class="sxs-lookup"><span data-stu-id="87ea6-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="87ea6-112">Dalším přístupem je <xref:System.Xml.XmlWriter>vytvoření a použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] možností zápisu <xref:System.Xml.XmlWriter>prvků do rozhraní .</span><span class="sxs-lookup"><span data-stu-id="87ea6-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="87ea6-113">Toto téma ukazuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="87ea6-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ea6-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea6-114">Example</span></span>  
 <span data-ttu-id="87ea6-115">Následující příklad vychází z příkladu v [části Postup: Streamovat fragmenty XML s přístupem k informacím záhlaví (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)</span><span class="sxs-lookup"><span data-stu-id="87ea6-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="87ea6-116">Tento příklad používá možnosti <xref:System.Xml.Linq.XStreamingElement> odložené spuštění k streamování výstupu.</span><span class="sxs-lookup"><span data-stu-id="87ea6-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="87ea6-117">Tento příklad může transformovat velmi velký dokument při zachování malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="87ea6-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="87ea6-118">Všimněte si,`StreamCustomerItem`že vlastní osa ( ) je `Customer` `Name`specificky `Item` napsána tak, že očekává dokument, který má , , a prvky a že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="87ea6-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="87ea6-119">Robustnější implementace by však byla připravena analyzovat neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="87ea6-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="87ea6-120">Následuje zdrojový dokument Source.xml:</span><span class="sxs-lookup"><span data-stu-id="87ea6-120">The following is the source document, Source.xml:</span></span>  
  
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
  
```vb  
Module Module1  
    Sub Main()  
        Dim root = New XStreamingElement("Root",  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
            )  
        root.Save("Test.xml")  
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))  
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
  
 <span data-ttu-id="87ea6-121">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="87ea6-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="87ea6-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea6-122">Example</span></span>  
 <span data-ttu-id="87ea6-123">Následující příklad také vychází z příkladu v [části Postup: Streamovat fragmenty XML s přístupem k informacím záhlaví (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)</span><span class="sxs-lookup"><span data-stu-id="87ea6-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="87ea6-124">Tento příklad používá [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] schopnost psát prvky do . <xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="87ea6-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="87ea6-125">Tento příklad může transformovat velmi velký dokument při zachování malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="87ea6-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="87ea6-126">Všimněte si,`StreamCustomerItem`že vlastní osa ( ) je `Customer` `Name`specificky `Item` napsána tak, že očekává dokument, který má , , a prvky a že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="87ea6-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="87ea6-127">Robustnější implementace by však buď ověřit zdrojový dokument s XSD, nebo by byla připravena analyzovat neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="87ea6-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="87ea6-128">Tento příklad používá stejný zdrojový dokument Source.xml jako předchozí příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="87ea6-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="87ea6-129">Také produkuje přesně stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="87ea6-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="87ea6-130">Použití <xref:System.Xml.Linq.XStreamingElement> pro streamování výstupního XML je <xref:System.Xml.XmlWriter>upřednostňováno před zápisem do .</span><span class="sxs-lookup"><span data-stu-id="87ea6-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim srcTree =  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
  
        Dim xws = New Xml.XmlWriterSettings()  
        xws.OmitXmlDeclaration = True  
        xws.Indent = True  
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)  
            xw.WriteStartElement("Root")  
            For Each el In srcTree  
                el.WriteTo(xw)  
            Next  
            xw.WriteEndElement()  
        End Using  
  
        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")  
        Console.WriteLine(s)  
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
  
 <span data-ttu-id="87ea6-131">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="87ea6-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87ea6-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="87ea6-132">See also</span></span>

- [<span data-ttu-id="87ea6-133">Rozšířené linq na xml programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87ea6-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
