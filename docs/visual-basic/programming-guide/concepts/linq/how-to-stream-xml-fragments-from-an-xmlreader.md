---
title: 'Postupy: streamování fragmentů XML ze třídy XmlReader'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 42d3edb390035d20f506388974000aa204312109
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636793"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="f32ae-102">Postupy: streamování fragmentů XML ze třídy XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f32ae-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="f32ae-103">V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="f32ae-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="f32ae-104">Toto téma ukazuje, jak streamovat fragmenty pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="f32ae-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="f32ae-105">Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení objektů <xref:System.Xml.Linq.XElement>, je napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="f32ae-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="f32ae-106">Metoda Axis obvykle vrací kolekci, například <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f32ae-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="f32ae-107">V metodě vlastní osy po vytvoření fragmentu XML voláním metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> vraťte kolekci pomocí `yield return`.</span><span class="sxs-lookup"><span data-stu-id="f32ae-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="f32ae-108">To poskytuje sémantiku pro odložené provádění vlastní metody osy.</span><span class="sxs-lookup"><span data-stu-id="f32ae-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="f32ae-109">Při vytváření stromu XML z objektu <xref:System.Xml.XmlReader> musí být <xref:System.Xml.XmlReader> umístěn na elementu.</span><span class="sxs-lookup"><span data-stu-id="f32ae-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="f32ae-110">Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nevrátí, dokud nepřečetla uzavírací značku elementu.</span><span class="sxs-lookup"><span data-stu-id="f32ae-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="f32ae-111">Chcete-li vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>, umístit čtecí modul na uzel, který chcete převést na <xref:System.Xml.Linq.XElement> stromu, a poté vytvořit objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f32ae-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="f32ae-112">Téma [Postupy: streamování fragmentů XML s přístupem k informacím hlavičky (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.</span><span class="sxs-lookup"><span data-stu-id="f32ae-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="f32ae-113">Téma [Postupy: provedení transformace streamování velkých dokumentů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.</span><span class="sxs-lookup"><span data-stu-id="f32ae-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f32ae-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f32ae-114">Example</span></span>  
 <span data-ttu-id="f32ae-115">Tento příklad vytvoří vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="f32ae-115">This example creates a custom axis method.</span></span> <span data-ttu-id="f32ae-116">Můžete se k němu dotázat pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="f32ae-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="f32ae-117">Vlastní metoda osy, `StreamRootChildDoc`, je metoda, která je určena specificky pro čtení dokumentu, který má opakující se `Child` element.</span><span class="sxs-lookup"><span data-stu-id="f32ae-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
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
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
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
  
 <span data-ttu-id="f32ae-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f32ae-118">This example produces the following output:</span></span>  
  
```console  
bbb  
ccc  
```  
  
 <span data-ttu-id="f32ae-119">V tomto příkladu je zdrojový dokument velmi malý.</span><span class="sxs-lookup"><span data-stu-id="f32ae-119">In this example, the source document is very small.</span></span> <span data-ttu-id="f32ae-120">Nicméně i v případě, že existovaly miliony `Child` prvků, bude mít tento příklad pořád malou paměť.</span><span class="sxs-lookup"><span data-stu-id="f32ae-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32ae-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f32ae-121">See also</span></span>

- [<span data-ttu-id="f32ae-122">Návod: implementace IEnumerable (Of T) v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f32ae-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [<span data-ttu-id="f32ae-123">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f32ae-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
