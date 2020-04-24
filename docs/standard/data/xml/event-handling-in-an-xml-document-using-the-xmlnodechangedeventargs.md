---
title: Zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
ms.openlocfilehash: b27c51572b1ba83480d90eba4add7f930715a4e5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156527"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="5b518-102">Zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="5b518-102">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>
<span data-ttu-id="5b518-103">**XmlNodeChangedEventArgs** zapouzdřuje argumenty předávané obslužným rutinám událostí registrovaným v objektu **XmlDocument** pro zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="5b518-103">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="5b518-104">Události a popis, kdy jsou aktivovány, jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="5b518-104">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="5b518-105">Událost</span><span class="sxs-lookup"><span data-stu-id="5b518-105">Event</span></span>|<span data-ttu-id="5b518-106">Aktiv</span><span class="sxs-lookup"><span data-stu-id="5b518-106">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="5b518-107">V případě, že bude uzel patřící do aktuálního dokumentu vložen do jiného uzlu.</span><span class="sxs-lookup"><span data-stu-id="5b518-107">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="5b518-108">Pokud byl uzel patřící do aktuálního dokumentu vložen do jiného uzlu.</span><span class="sxs-lookup"><span data-stu-id="5b518-108">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="5b518-109">V případě, že bude uzel patřící do tohoto dokumentu odebrán z dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5b518-109">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="5b518-110">Pokud byl uzel patřící do tohoto dokumentu odebrán z jeho nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="5b518-110">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="5b518-111">Když se bude měnit hodnota uzlu.</span><span class="sxs-lookup"><span data-stu-id="5b518-111">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="5b518-112">Při změně hodnoty uzlu.</span><span class="sxs-lookup"><span data-stu-id="5b518-112">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="5b518-113">Pokud je využití paměti **objektu XmlDataDocument** plně optimalizované tak, aby používalo úložiště **DataSet** , nemusí **objektu XmlDataDocument** po provedení změn v podkladové **datové sadě**vyvolat žádnou z výše uvedených událostí.</span><span class="sxs-lookup"><span data-stu-id="5b518-113">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="5b518-114">Pokud tyto události potřebujete, je nutné projít celým **třídou XmlDocument** , aby bylo využití paměti neplně optimalizované.</span><span class="sxs-lookup"><span data-stu-id="5b518-114">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="5b518-115">Následující příklad kódu ukazuje, jak definovat obslužnou rutinu události a jak přidat obslužnou rutinu události do události.</span><span class="sxs-lookup"><span data-stu-id="5b518-115">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)
AddHandler doc.NodeInserted, XmlNodeChgEHdlr
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 <span data-ttu-id="5b518-116">Některé operace XML model DOM (Document Object Model) (DOM) jsou složené operace, které mohou vést k vyvolání více událostí.</span><span class="sxs-lookup"><span data-stu-id="5b518-116">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="5b518-117">Například **AppendChild** může také odebrat uzel, který je připojený z předchozího nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="5b518-117">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="5b518-118">V takovém případě se zobrazí událost **NodeRemoved** , která následuje po události **NodeInserted** .</span><span class="sxs-lookup"><span data-stu-id="5b518-118">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="5b518-119">Operace, jako je nastavení **InnerXml** , by mohly vést k několika událostem.</span><span class="sxs-lookup"><span data-stu-id="5b518-119">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="5b518-120">Následující příklad kódu ukazuje vytvoření obslužné rutiny události a zpracování události **NodeInserted** .</span><span class="sxs-lookup"><span data-stu-id="5b518-120">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class
```  
  
 <span data-ttu-id="5b518-121">Další informace naleznete v tématech <xref:System.Xml.XmlNodeChangedEventArgs> a <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="5b518-121">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b518-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b518-122">See also</span></span>

- [<span data-ttu-id="5b518-123">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5b518-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
