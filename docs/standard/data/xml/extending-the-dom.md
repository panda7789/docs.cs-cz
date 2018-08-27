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
ms.openlocfilehash: 58f32dcb76246bed1030f3d0a45db2541f381877
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908264"
---
# <a name="extending-the-dom"></a>Rozšíření modelu DOM

Rozhraní Microsoft .NET Framework obsahuje základní sadu tříd, který poskytuje implementaci z XML Document Object Model (DOM). <xref:System.Xml.XmlNode>a její odvozené třídy, poskytuje metody a vlastnosti, které vám umožní přejít, dotazování a modifikaci obsahu a struktury dokumentu XML.

Obsah XML je načtena do paměti pomocí modelu DOM, uzly vytvořené obsahují informace, jako je název uzlu, typ uzlu a tak dále. Může nastat situace, kdy potřebujete konkrétní uzel informace, které se neposkytuje základní třídy. Můžete například zobrazit číslo řádku a pozice uzlu. V takovém případě lze odvozovat nové třídy z existujících tříd modelu DOM a přidat další funkce.

Existují dvě obecné pokyny, kdy odvození nové třídy:

- Doporučuje se, že nikdy odvozujete od <xref:System.Xml.XmlNode> třídy. Místo toho se doporučuje odvození třídy z třídy odpovídající typ uzlu, které vás zajímají. Například pokud chcete vrátit další informace o uzlů atributů, které lze odvodit z <xref:System.Xml.XmlAttribute> třídy.

- S výjimkou metody vytvoření uzlu se doporučuje, při přepisování funkce, abyste vždy volat základní verzi funkce a přidejte jakékoli další zpracování.

## <a name="creating-your-own-node-instances"></a>Vytvoření vlastní instance uzlu

<xref:System.Xml.XmlDocument> Třída obsahuje metody vytvoření uzlu. Při načítání souboru XML tyto metody jsou volány k vytvoření uzly. Tyto metody můžete přepsat tak, aby vaše instance uzlu jsou vytvořeny při načtení dokumentu. Například, pokud jste rozšířili <xref:System.Xml.XmlElement> třídy by zdědil <xref:System.Xml.XmlDocument> třídy a přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metody.

Následující příklad ukazuje, jak přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metody, která vrátí implementaci <xref:System.Xml.XmlElement> třídy.

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

Chcete-li rozšířit třídu, odvození od některého ze existujících tříd modelu DOM vaší třídy. Můžete přepsat virtuální metody nebo vlastnosti v základní třídě nebo přidejte vlastní.

V následujícím příkladu je nová třída vytvořen, která implementuje <xref:System.Xml.XmlElement> třídy a <xref:System.Xml.IXmlLineInfo> rozhraní. Další metody a vlastnosti jsou definovány, což umožňuje uživatelům shromažďovat informace o řádku.

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

Následující příklad vrátí počet prvků v dokumentu XML:

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

#### <a name="input"></a>Vstup

Book.XML

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

Implementace rozhraní .NET Framework v modelu DOM obsahuje také událostí systému, který vám umožní přijímat a zpracovávat události při změně uzly v dokumentu XML. Použití <xref:System.Xml.XmlNodeChangedEventHandler> a <xref:System.Xml.XmlNodeChangedEventArgs> třídy, můžete zachytit `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, a `NodeRemoving` události.

Zpracování událostí proces funguje stejně v odvozených třídách stejně jako v původní třídy modelu DOM.

Další informace o zpracování událostí uzlu, naleznete v tématu [události](../../../../docs/standard/events/index.md) a <xref:System.Xml.XmlNodeChangedEventHandler>.

## <a name="default-attributes-and-the-createelement-method"></a>Výchozí atributy a CreateElement – metoda

Pokud vám přepsání <xref:System.Xml.XmlDocument.CreateElement%2A> metoda v odvozené třídě, výchozí atributy nejsou přidány při vytváření nové prvky při úpravě dokumentu. Toto je problém, pouze při úpravách. Protože <xref:System.Xml.XmlDocument.CreateElement%2A> metoda je zodpovědný za přidání výchozích atributů, které mají <xref:System.Xml.XmlDocument>, musí kód této funkce v <xref:System.Xml.XmlDocument.CreateElement%2A> metoda. Pokud načítáte <xref:System.Xml.XmlDocument> , který obsahuje výchozí atributy, se budou zpracovávat správně. Další informace o výchozí atributy, naleznete v tématu [vytváření nových atributů pro elementy v modelu DOM](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Viz také

[Model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)  
