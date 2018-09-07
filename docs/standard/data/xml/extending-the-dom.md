---
title: Rozšíření modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70e13893cf350a193411f1833e2e3b21c9b64182
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061062"
---
# <a name="extending-the-dom"></a><span data-ttu-id="f795a-102">Rozšíření modelu DOM</span><span class="sxs-lookup"><span data-stu-id="f795a-102">Extending the DOM</span></span>

<span data-ttu-id="f795a-103">Rozhraní Microsoft .NET Framework obsahuje základní sadu tříd, který poskytuje implementaci z XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="f795a-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="f795a-104"><xref:System.Xml.XmlNode>a její odvozené třídy, poskytuje metody a vlastnosti, které vám umožní přejít, dotazování a modifikaci obsahu a struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f795a-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="f795a-105">Obsah XML je načtena do paměti pomocí modelu DOM, uzly vytvořené obsahují informace, jako je název uzlu, typ uzlu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f795a-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="f795a-106">Může nastat situace, kdy potřebujete konkrétní uzel informace, které se neposkytuje základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f795a-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="f795a-107">Můžete například zobrazit číslo řádku a pozice uzlu.</span><span class="sxs-lookup"><span data-stu-id="f795a-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="f795a-108">V takovém případě lze odvozovat nové třídy z existujících tříd modelu DOM a přidat další funkce.</span><span class="sxs-lookup"><span data-stu-id="f795a-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="f795a-109">Existují dvě obecné pokyny, kdy odvození nové třídy:</span><span class="sxs-lookup"><span data-stu-id="f795a-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="f795a-110">Doporučuje se, že nikdy odvozujete od <xref:System.Xml.XmlNode> třídy.</span><span class="sxs-lookup"><span data-stu-id="f795a-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="f795a-111">Místo toho se doporučuje odvození třídy z třídy odpovídající typ uzlu, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="f795a-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="f795a-112">Například pokud chcete vrátit další informace o uzlů atributů, které lze odvodit z <xref:System.Xml.XmlAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="f795a-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="f795a-113">S výjimkou metody vytvoření uzlu se doporučuje, při přepisování funkce, abyste vždy volat základní verzi funkce a přidejte jakékoli další zpracování.</span><span class="sxs-lookup"><span data-stu-id="f795a-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="f795a-114">Vytvoření vlastní instance uzlu</span><span class="sxs-lookup"><span data-stu-id="f795a-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="f795a-115"><xref:System.Xml.XmlDocument> Třída obsahuje metody vytvoření uzlu.</span><span class="sxs-lookup"><span data-stu-id="f795a-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="f795a-116">Při načítání souboru XML tyto metody jsou volány k vytvoření uzly.</span><span class="sxs-lookup"><span data-stu-id="f795a-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="f795a-117">Tyto metody můžete přepsat tak, aby vaše instance uzlu jsou vytvořeny při načtení dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f795a-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="f795a-118">Například, pokud jste rozšířili <xref:System.Xml.XmlElement> třídy by zdědil <xref:System.Xml.XmlDocument> třídy a přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f795a-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="f795a-119">Následující příklad ukazuje, jak přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metody, která vrátí implementaci <xref:System.Xml.XmlElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="f795a-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument 
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI) 
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a><span data-ttu-id="f795a-120">Rozšíření třídy</span><span class="sxs-lookup"><span data-stu-id="f795a-120">Extending a Class</span></span>

<span data-ttu-id="f795a-121">Chcete-li rozšířit třídu, odvození od některého ze existujících tříd modelu DOM vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="f795a-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="f795a-122">Můžete přepsat virtuální metody nebo vlastnosti v základní třídě nebo přidejte vlastní.</span><span class="sxs-lookup"><span data-stu-id="f795a-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="f795a-123">V následujícím příkladu je nová třída vytvořen, která implementuje <xref:System.Xml.XmlElement> třídy a <xref:System.Xml.IXmlLineInfo> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f795a-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="f795a-124">Další metody a vlastnosti jsou definovány, což umožňuje uživatelům shromažďovat informace o řádku.</span><span class="sxs-lookup"><span data-stu-id="f795a-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a><span data-ttu-id="f795a-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="f795a-125">Example</span></span>

<span data-ttu-id="f795a-126">Následující příklad vrátí počet prvků v dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="f795a-126">The following example counts the number of elements in an XML document:</span></span>

```vb
Imports System
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a><span data-ttu-id="f795a-127">Vstup</span><span class="sxs-lookup"><span data-stu-id="f795a-127">Input</span></span>

<span data-ttu-id="f795a-128">Book.XML</span><span class="sxs-lookup"><span data-stu-id="f795a-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="f795a-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="f795a-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="f795a-130">Obslužná rutina události uzlu</span><span class="sxs-lookup"><span data-stu-id="f795a-130">Node Event Handler</span></span>

<span data-ttu-id="f795a-131">Implementace rozhraní .NET Framework v modelu DOM obsahuje také událostí systému, který vám umožní přijímat a zpracovávat události při změně uzly v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f795a-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="f795a-132">Použití <xref:System.Xml.XmlNodeChangedEventHandler> a <xref:System.Xml.XmlNodeChangedEventArgs> třídy, můžete zachytit `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, a `NodeRemoving` události.</span><span class="sxs-lookup"><span data-stu-id="f795a-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="f795a-133">Zpracování událostí proces funguje stejně v odvozených třídách stejně jako v původní třídy modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="f795a-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="f795a-134">Další informace o zpracování událostí uzlu, naleznete v tématu [události](../../../../docs/standard/events/index.md) a <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f795a-134">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="f795a-135">Výchozí atributy a CreateElement – metoda</span><span class="sxs-lookup"><span data-stu-id="f795a-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="f795a-136">Pokud vám přepsání <xref:System.Xml.XmlDocument.CreateElement%2A> metoda v odvozené třídě, výchozí atributy nejsou přidány při vytváření nové prvky při úpravě dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f795a-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="f795a-137">Toto je problém, pouze při úpravách.</span><span class="sxs-lookup"><span data-stu-id="f795a-137">This is only an issue while editing.</span></span> <span data-ttu-id="f795a-138">Protože <xref:System.Xml.XmlDocument.CreateElement%2A> metoda je zodpovědný za přidání výchozích atributů, které mají <xref:System.Xml.XmlDocument>, musí kód této funkce v <xref:System.Xml.XmlDocument.CreateElement%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f795a-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="f795a-139">Pokud načítáte <xref:System.Xml.XmlDocument> , který obsahuje výchozí atributy, se budou zpracovávat správně.</span><span class="sxs-lookup"><span data-stu-id="f795a-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="f795a-140">Další informace o výchozí atributy, naleznete v tématu [vytváření nových atributů pro elementy v modelu DOM](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="f795a-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f795a-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f795a-141">See also</span></span>

- [<span data-ttu-id="f795a-142">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f795a-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
