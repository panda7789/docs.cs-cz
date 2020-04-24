---
title: Rozšíření modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 11c7e8c8d2ea3b49fe73ab4dde4e2ccc8bc917ff
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159673"
---
# <a name="extending-the-dom"></a>Rozšíření modelu DOM

Microsoft .NET Framework obsahuje základní sadu tříd, které poskytují implementaci XML model DOM (Document Object Model) (DOM). <xref:System.Xml.XmlNode>A jeho odvozené třídy poskytuje metody a vlastnosti, které umožňují procházení, dotazování a úpravu obsahu a struktury dokumentu XML.

Když je obsah XML načten do paměti pomocí modelu DOM, vytvořené uzly obsahují informace, jako je název uzlu, typ uzlu a tak dále. Můžou nastat případy, kdy potřebujete konkrétní informace o uzlu, které neposkytují základní třídy. Například může být vhodné zobrazit číslo řádku a umístění uzlu. V takovém případě můžete odvodit nové třídy z existujících tříd modelu DOM a přidat další funkce.

Při odvozování nových tříd jsou k dispozici dva obecné pokyny:

- Doporučuje se nikdy odvozovat od <xref:System.Xml.XmlNode> třídy. Místo toho se doporučuje odvodit třídy z třídy odpovídající typu uzlu, který vás zajímá. Například pokud chcete získat další informace o uzlech atributů, můžete odvozovat z <xref:System.Xml.XmlAttribute> třídy.

- S výjimkou metod vytváření uzlů doporučujeme, aby při přepsání funkce vždy volali základní verzi funkce a pak přidali jakékoli další zpracování.

## <a name="creating-your-own-node-instances"></a>Vytváření vlastních instancí uzlů

<xref:System.Xml.XmlDocument> Třída obsahuje metody vytváření uzlů. Když je načten soubor XML, jsou volány tyto metody pro vytvoření uzlů. Tyto metody můžete přepsat tak, aby se při načtení dokumentu vytvořily instance uzlů. Například pokud jste rozšířili <xref:System.Xml.XmlElement> třídu, měli byste <xref:System.Xml.XmlDocument> třídu dědit a přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metodu.

Následující příklad ukazuje, jak přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metodu pro vrácení vaší implementace <xref:System.Xml.XmlElement> třídy.

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

## <a name="extending-a-class"></a>Rozšíření třídy

Chcete-li zvětšit třídu, odvodíte třídu z jedné z existujících tříd modelu DOM. Pak můžete přepsat všechny virtuální metody nebo vlastnosti v základní třídě nebo přidat vlastní.

V následujícím příkladu je vytvořena nová třída, která implementuje <xref:System.Xml.XmlElement> třídu a <xref:System.Xml.IXmlLineInfo> rozhraní. Jsou definovány další metody a vlastnosti, které umožňují uživatelům shromažďovat informace o řádcích.

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

### <a name="example"></a>Příklad

Následující příklad spočítá počet prvků v dokumentu XML:

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

#### <a name="input"></a>Vstup

Book. XML

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a>Výstup

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a>Obslužná rutina události uzlu

.NET Framework implementace modelu DOM také obsahuje systém událostí, který umožňuje přijímat a zpracovávat události při změně uzlů v dokumentu XML. Pomocí tříd <xref:System.Xml.XmlNodeChangedEventHandler> a <xref:System.Xml.XmlNodeChangedEventArgs> můžete `NodeChanged`zachytit `NodeChanging`události, `NodeInserted`,, `NodeInserting`, `NodeRemoved`a. `NodeRemoving`

Proces zpracování událostí funguje v odvozených třídách úplně stejně, jako by to bylo v původních třídách modelu DOM.

Další informace o zpracování událostí uzlu naleznete v tématu [události](../../../../docs/standard/events/index.md) a <xref:System.Xml.XmlNodeChangedEventHandler>.

## <a name="default-attributes-and-the-createelement-method"></a>Výchozí atributy a metoda CreateElement

Pokud přepíšete <xref:System.Xml.XmlDocument.CreateElement%2A> metodu v odvozené třídě, při vytváření nových prvků při úpravách dokumentu nebudou přidány výchozí atributy. Jedná se o problém jenom při úpravách. Vzhledem k <xref:System.Xml.XmlDocument.CreateElement%2A> tomu <xref:System.Xml.XmlDocument>, že metoda je zodpovědná za přidání výchozích atributů do, musíte tuto funkci v <xref:System.Xml.XmlDocument.CreateElement%2A> metodě nakódovat. Pokud načítáte <xref:System.Xml.XmlDocument> , který obsahuje výchozí atributy, bude zpracována správně. Další informace o výchozích atributech naleznete v tématu [vytváření nových atributů pro prvky v modelu DOM](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
