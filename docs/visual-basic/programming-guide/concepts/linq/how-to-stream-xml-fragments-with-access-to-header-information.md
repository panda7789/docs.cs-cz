---
title: 'Postupy: Streamování fragmentů XML pomocí přístupu k informacím hlavičky'
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 8d0543ff5a772768292c0e3117f41bea9367d23a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397684"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="bcf45-102">Postupy: streamování fragmentů XML s přístupem k informacím hlavičky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcf45-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="bcf45-103">Někdy je nutné číst libovolně velké soubory XML a napsat aplikaci tak, aby paměti aplikace byly předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="bcf45-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="bcf45-104">Pokud se pokusíte naplnit strom XML velkým souborem XML, využití paměti bude úměrné velikosti souboru, tedy nadměrné.</span><span class="sxs-lookup"><span data-stu-id="bcf45-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="bcf45-105">Proto byste měli místo toho použít metodu streamování.</span><span class="sxs-lookup"><span data-stu-id="bcf45-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="bcf45-106">Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="bcf45-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="bcf45-107">Můžete však chtít použít LINQ k dotazování stromu XML.</span><span class="sxs-lookup"><span data-stu-id="bcf45-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="bcf45-108">Pokud se jedná o tento případ, můžete napsat vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="bcf45-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="bcf45-109">Další informace naleznete v tématu [How to: Write a LINQ to XML Axis Method (Visual Basic)](how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="bcf45-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="bcf45-110">Chcete-li napsat vlastní metodu osy, napíšete malou metodu, která používá <xref:System.Xml.XmlReader> ke čtení uzlů, dokud nedosáhne jednoho z uzlů, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="bcf45-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="bcf45-111">Metoda pak volá <xref:System.Xml.Linq.XNode.ReadFrom%2A> , který čte z <xref:System.Xml.XmlReader> a vytvoří instanci XML fragmentu.</span><span class="sxs-lookup"><span data-stu-id="bcf45-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="bcf45-112">Pak můžete napsat dotazy LINQ na vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="bcf45-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="bcf45-113">Techniky streamování se nejlépe aplikují v situacích, kdy potřebujete zpracovat zdrojový dokument jenom jednou, a můžete zpracovat elementy v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="bcf45-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="bcf45-114">Některé standardní operátory pro dotazování, jako <xref:System.Linq.Enumerable.OrderBy%2A> je například iterace zdroje, shromáždění všech dat, jejich řazení a nakonec vydávají první položku v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="bcf45-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="bcf45-115">Všimněte si, že pokud použijete operátor dotazu, který materializuje svůj zdroj před tím, než zadáte první položku, nebudete si uchovávat malý objem paměti.</span><span class="sxs-lookup"><span data-stu-id="bcf45-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcf45-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcf45-116">Example</span></span>  
 <span data-ttu-id="bcf45-117">Někdy je problém jenom trochu zajímavější.</span><span class="sxs-lookup"><span data-stu-id="bcf45-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="bcf45-118">V následujícím dokumentu XML musí příjemce vlastní metody osy také znát název zákazníka, ke kterému každá položka patří.</span><span class="sxs-lookup"><span data-stu-id="bcf45-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="bcf45-119">Přístup v tomto příkladu je také sledován pro tyto informace hlavičky, uložení informací v hlavičce a následné sestavení malého stromu XML, který obsahuje jak informace v hlavičce, tak i podrobnosti, které provádíte ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="bcf45-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="bcf45-120">Metoda Axis pak tento nový malý strom XML.</span><span class="sxs-lookup"><span data-stu-id="bcf45-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="bcf45-121">Dotaz pak má přístup k informacím v hlavičce a také k podrobným informacím.</span><span class="sxs-lookup"><span data-stu-id="bcf45-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="bcf45-122">Tento přístup má malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="bcf45-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="bcf45-123">Vzhledem k tomu, že se přestanou fragmenty XML, nezachovají se žádné odkazy na předchozí fragment a je k dispozici pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bcf45-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="bcf45-124">Všimněte si, že tato technika vytváří mnoho krátkodobých objektů v haldě.</span><span class="sxs-lookup"><span data-stu-id="bcf45-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="bcf45-125">Následující příklad ukazuje, jak implementovat a použít vlastní metodu osy, která streamuje fragmenty XML ze souboru určeného identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="bcf45-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="bcf45-126">Tato vlastní osa je určena konkrétně tak, že očekává dokument, který obsahuje `Customer` `Name` prvky, a a `Item` že tyto prvky budou uspořádány jako v `Source.xml` dokumentu výše.</span><span class="sxs-lookup"><span data-stu-id="bcf45-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="bcf45-127">Jedná se o zjednodušený implementaci.</span><span class="sxs-lookup"><span data-stu-id="bcf45-127">It is a simplistic implementation.</span></span> <span data-ttu-id="bcf45-128">Robustnější implementace by se připravila k analýze neplatného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bcf45-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="bcf45-129">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bcf45-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bcf45-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcf45-130">See also</span></span>

- [<span data-ttu-id="bcf45-131">Rozšířené programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcf45-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
