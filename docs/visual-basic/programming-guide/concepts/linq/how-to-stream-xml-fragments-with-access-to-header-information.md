---
title: "Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f745d0725b9b05620b4b967e51b452e54fe5e6d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="03ad3-102">Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03ad3-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="03ad3-103">Někdy je nutné ke čtení libovolně velké soubory XML a zapisovat vaše aplikace tak, aby nároky na paměť pro aplikace je předvídatelný.</span><span class="sxs-lookup"><span data-stu-id="03ad3-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="03ad3-104">Pokud se pokusíte strom XML naplnění velký soubor XML, bude vaše využití paměti velikosti souboru – to znamená, nadměrné.</span><span class="sxs-lookup"><span data-stu-id="03ad3-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="03ad3-105">Proto byste měli místo toho používat streamování techniku.</span><span class="sxs-lookup"><span data-stu-id="03ad3-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="03ad3-106">Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="03ad3-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="03ad3-107">Ale můžete chtít použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k dotazování stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="03ad3-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="03ad3-108">Pokud je to tento případ, můžete napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="03ad3-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="03ad3-109">Další informace najdete v tématu [postupy: zápis LINQ metodě osy XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="03ad3-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="03ad3-110">Zápis způsob osy, zápis malých metody, která používá <xref:System.Xml.XmlReader> číst uzlů, dokud nebude dosaženo jednoho z uzlů, které vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="03ad3-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="03ad3-111">Pak zavolá metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A>, který čte z <xref:System.Xml.XmlReader> a vytvoří XML fragment.</span><span class="sxs-lookup"><span data-stu-id="03ad3-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="03ad3-112">Poté můžete napsat dotazů LINQ na metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="03ad3-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="03ad3-113">Streamování techniky nejlépe použity v situacích, kdy je potřeba zpracovat zdrojový dokument jenom jednou a může zpracovat elementy v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="03ad3-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="03ad3-114">Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iteraci zdrojových, shromáždit všechna data, řazení ji a nakonec yield první položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="03ad3-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="03ad3-115">Všimněte si, pokud používáte operátor dotazu, který bude realizována zdrojem před je první položka, nebude zachovali malou paměťovou zátěž.</span><span class="sxs-lookup"><span data-stu-id="03ad3-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03ad3-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="03ad3-116">Example</span></span>  
 <span data-ttu-id="03ad3-117">Někdy problém získá jen málo další zajímavé.</span><span class="sxs-lookup"><span data-stu-id="03ad3-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="03ad3-118">V následujícím dokumentu XML má příjemce metodu vlastní osy také znát název zákazníka, které patří každou položku.</span><span class="sxs-lookup"><span data-stu-id="03ad3-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="03ad3-119">Přístup, který má v tomto příkladu je také sledovat informace hlavičky, uložit informace ze záhlaví a následně vytvořit malé stromu XML, který obsahuje informace v záhlaví a podrobností, která jsou vytváření výčtu.</span><span class="sxs-lookup"><span data-stu-id="03ad3-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="03ad3-120">Metoda osy poskytuje pak tento nový, malé strom XML.</span><span class="sxs-lookup"><span data-stu-id="03ad3-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="03ad3-121">Dotaz pak má přístup k informace hlavičky, jakož i podrobné informace.</span><span class="sxs-lookup"><span data-stu-id="03ad3-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="03ad3-122">Tento přístup má malou paměťovou zátěž.</span><span class="sxs-lookup"><span data-stu-id="03ad3-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="03ad3-123">Každý fragment XML podrobností, je vhodné, jsou uchovány žádné odkazy na předchozí fragment, a je k dispozici pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="03ad3-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="03ad3-124">Všimněte si, že tento postup vytvoří mnoho zkrátí objektů v haldě.</span><span class="sxs-lookup"><span data-stu-id="03ad3-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="03ad3-125">Následující příklad ukazuje, jak implementovat a použít vlastní osy metodu, která datové proudy fragmenty XML ze souboru určeného identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="03ad3-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="03ad3-126">Tato vlastní osy je speciálně tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` elementy a aby tyto prvky se být uspořádány jako výše `Source.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="03ad3-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="03ad3-127">Je zneužívající vlastností prohlížeče implementace.</span><span class="sxs-lookup"><span data-stu-id="03ad3-127">It is a simplistic implementation.</span></span> <span data-ttu-id="03ad3-128">Robustnější implementace by připravený k analýze neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="03ad3-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="03ad3-129">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="03ad3-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03ad3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="03ad3-130">See Also</span></span>  
 [<span data-ttu-id="03ad3-131">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03ad3-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
