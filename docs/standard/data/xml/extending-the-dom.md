---
title: Rozšíření modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 4a1a7af0e841601542a30c7bd3f71395faa6cb57
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287789"
---
# <a name="extending-the-dom"></a><span data-ttu-id="2e664-102">Rozšíření modelu DOM</span><span class="sxs-lookup"><span data-stu-id="2e664-102">Extending the DOM</span></span>

<span data-ttu-id="2e664-103">Microsoft .NET Framework obsahuje základní sadu tříd, které poskytují implementaci XML model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="2e664-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="2e664-104"><xref:System.Xml.XmlNode>A jeho odvozené třídy poskytuje metody a vlastnosti, které umožňují procházení, dotazování a úpravu obsahu a struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2e664-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="2e664-105">Když je obsah XML načten do paměti pomocí modelu DOM, vytvořené uzly obsahují informace, jako je název uzlu, typ uzlu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2e664-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="2e664-106">Můžou nastat případy, kdy potřebujete konkrétní informace o uzlu, které neposkytují základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2e664-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="2e664-107">Například může být vhodné zobrazit číslo řádku a umístění uzlu.</span><span class="sxs-lookup"><span data-stu-id="2e664-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="2e664-108">V takovém případě můžete odvodit nové třídy z existujících tříd modelu DOM a přidat další funkce.</span><span class="sxs-lookup"><span data-stu-id="2e664-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="2e664-109">Při odvozování nových tříd jsou k dispozici dva obecné pokyny:</span><span class="sxs-lookup"><span data-stu-id="2e664-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="2e664-110">Doporučuje se nikdy odvozovat od <xref:System.Xml.XmlNode> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e664-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="2e664-111">Místo toho se doporučuje odvodit třídy z třídy odpovídající typu uzlu, který vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="2e664-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="2e664-112">Například pokud chcete získat další informace o uzlech atributů, můžete odvozovat z <xref:System.Xml.XmlAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e664-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="2e664-113">S výjimkou metod vytváření uzlů doporučujeme, aby při přepsání funkce vždy volali základní verzi funkce a pak přidali jakékoli další zpracování.</span><span class="sxs-lookup"><span data-stu-id="2e664-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="2e664-114">Vytváření vlastních instancí uzlů</span><span class="sxs-lookup"><span data-stu-id="2e664-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="2e664-115"><xref:System.Xml.XmlDocument>Třída obsahuje metody vytváření uzlů.</span><span class="sxs-lookup"><span data-stu-id="2e664-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="2e664-116">Když je načten soubor XML, jsou volány tyto metody pro vytvoření uzlů.</span><span class="sxs-lookup"><span data-stu-id="2e664-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="2e664-117">Tyto metody můžete přepsat tak, aby se při načtení dokumentu vytvořily instance uzlů.</span><span class="sxs-lookup"><span data-stu-id="2e664-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="2e664-118">Například pokud jste rozšířili <xref:System.Xml.XmlElement> třídu, měli byste <xref:System.Xml.XmlDocument> třídu dědit a přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="2e664-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="2e664-119">Následující příklad ukazuje, jak přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metodu pro vrácení vaší implementace <xref:System.Xml.XmlElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e664-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

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

## <a name="extending-a-class"></a><span data-ttu-id="2e664-120">Rozšíření třídy</span><span class="sxs-lookup"><span data-stu-id="2e664-120">Extending a Class</span></span>

<span data-ttu-id="2e664-121">Chcete-li zvětšit třídu, odvodíte třídu z jedné z existujících tříd modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="2e664-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="2e664-122">Pak můžete přepsat všechny virtuální metody nebo vlastnosti v základní třídě nebo přidat vlastní.</span><span class="sxs-lookup"><span data-stu-id="2e664-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="2e664-123">V následujícím příkladu je vytvořena nová třída, která implementuje <xref:System.Xml.XmlElement> třídu a <xref:System.Xml.IXmlLineInfo> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2e664-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="2e664-124">Jsou definovány další metody a vlastnosti, které umožňují uživatelům shromažďovat informace o řádcích.</span><span class="sxs-lookup"><span data-stu-id="2e664-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

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

### <a name="example"></a><span data-ttu-id="2e664-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e664-125">Example</span></span>

<span data-ttu-id="2e664-126">Následující příklad spočítá počet prvků v dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="2e664-126">The following example counts the number of elements in an XML document:</span></span>

```vb
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

#### <a name="input"></a><span data-ttu-id="2e664-127">Vstup</span><span class="sxs-lookup"><span data-stu-id="2e664-127">Input</span></span>

<span data-ttu-id="2e664-128">Book. XML</span><span class="sxs-lookup"><span data-stu-id="2e664-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="2e664-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="2e664-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="2e664-130">Obslužná rutina události uzlu</span><span class="sxs-lookup"><span data-stu-id="2e664-130">Node Event Handler</span></span>

<span data-ttu-id="2e664-131">.NET Framework implementace modelu DOM také obsahuje systém událostí, který umožňuje přijímat a zpracovávat události při změně uzlů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2e664-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="2e664-132">Pomocí <xref:System.Xml.XmlNodeChangedEventHandler> tříd a <xref:System.Xml.XmlNodeChangedEventArgs> můžete zachytit `NodeChanged` události,,, `NodeChanging` `NodeInserted` `NodeInserting` , `NodeRemoved` a `NodeRemoving` .</span><span class="sxs-lookup"><span data-stu-id="2e664-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="2e664-133">Proces zpracování událostí funguje v odvozených třídách úplně stejně, jako by to bylo v původních třídách modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="2e664-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="2e664-134">Další informace o zpracování událostí uzlu naleznete v tématu [události](../../events/index.md) a <xref:System.Xml.XmlNodeChangedEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="2e664-134">For more information regarding node event handling, see [Events](../../events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="2e664-135">Výchozí atributy a metoda CreateElement</span><span class="sxs-lookup"><span data-stu-id="2e664-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="2e664-136">Pokud přepíšete <xref:System.Xml.XmlDocument.CreateElement%2A> metodu v odvozené třídě, při vytváření nových prvků při úpravách dokumentu nebudou přidány výchozí atributy.</span><span class="sxs-lookup"><span data-stu-id="2e664-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="2e664-137">Jedná se o problém jenom při úpravách.</span><span class="sxs-lookup"><span data-stu-id="2e664-137">This is only an issue while editing.</span></span> <span data-ttu-id="2e664-138">Vzhledem k tomu <xref:System.Xml.XmlDocument.CreateElement%2A> , že metoda je zodpovědná za přidání výchozích atributů do <xref:System.Xml.XmlDocument> , musíte tuto funkci v metodě nakódovat <xref:System.Xml.XmlDocument.CreateElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="2e664-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="2e664-139">Pokud načítáte <xref:System.Xml.XmlDocument> , který obsahuje výchozí atributy, bude zpracována správně.</span><span class="sxs-lookup"><span data-stu-id="2e664-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="2e664-140">Další informace o výchozích atributech naleznete v tématu [vytváření nových atributů pro prvky v modelu DOM](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="2e664-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e664-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e664-141">See also</span></span>

- [<span data-ttu-id="2e664-142">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2e664-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
