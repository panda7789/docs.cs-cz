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
ms.openlocfilehash: 93821b844d35f005afa1702e4f7922ca1320c962
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572249"
---
# <a name="extending-the-dom"></a>Rozšíření modelu DOM
Rozhraní Microsoft .NET Framework obsahuje základní sadu třídy, která poskytuje implementaci z XML modelu DOM (Document Object). <xref:System.Xml.XmlNode>a jeho odvozené třídy, poskytuje metody a vlastnosti, které vám umožní přejít, dotazování a změnit obsah a struktura dokumentu XML.  
  
 Když obsah XML je načten do paměti pomocí modelu DOM, uzlů vytvořené obsahují informace jako název uzlu, typ uzlu a tak dále. Mohou nastat situace kde potřebujete informace o konkrétním uzlu, které neposkytuje základní třídy. Můžete například zobrazit číslo řádku a pozice uzlu. V takovém případě můžete odvozovat z existujících tříd DOM novou a přidat další funkce.  
  
 Existují dvě obecné pokyny při jeho odvozování nové třídy:  
  
-   Doporučuje se, že nikdy odvozujete od <xref:System.Xml.XmlNode> třídy. Doporučuje se místo toho odvodit třídy od třídy odpovídající typ uzlu, který vás zajímá. Například pokud chcete vrátit další informace na atribut uzly, můžete odvozujete od <xref:System.Xml.XmlAttribute> třídy.  
  
-   S výjimkou metody vytvoření uzlu se doporučuje, když přepisování funkce, abyste vždy volat základní verze funkce a pak přidat žádné další zpracování.  
  
## <a name="creating-your-own-node-instances"></a>Vytvoření vlastního uzlu instancí  
 <xref:System.Xml.XmlDocument> Třída obsahuje metody pro vytvoření uzlu. Při načítání souboru XML, se nazývají tyto metody pro vytvoření uzly. Tyto metody můžete přepsat tak, aby vaše instance uzlu se vytvoří při načtení dokumentu. Například, pokud jste rozšířili <xref:System.Xml.XmlElement> třída, by dědění <xref:System.Xml.XmlDocument> třídy a přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metoda.  
  
 Následující příklad ukazuje, jak lze přepsat <xref:System.Xml.XmlDocument.CreateElement%2A> metoda vrátí vaši implementaci <xref:System.Xml.XmlElement> třídy.  
  
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
class LineInfoDocument : XmlDocument {  
  public override XmlElement CreateElement(string prefix, string localname, string nsURI) {  
  LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);  
  return elem;  
  }  
```  
  
## <a name="extending-a-class"></a>Rozšíření třídy  
 Rozšířit třídu, odvodíte z jednoho z existujících tříd DOM třídě. Potom můžete přepsat virtuální metody nebo vlastnosti v základní třídě nebo přidat vlastní.  
  
 V následujícím příkladu je novou třídu vytvořili, který implementuje <xref:System.Xml.XmlElement> třídy a <xref:System.Xml.IXmlLineInfo> rozhraní. Další metody a vlastnosti jsou definovány, což umožňuje uživatelům získat informace o řádku.  
  
```vb  
Class LineInfoElement  
   Inherits XmlElement  
   Implements IXmlLineInfo  
   Private lineNumber As Integer = 0  
   Private linePosition As Integer = 0  
  
   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)  
      MyBase.New(prefix, localname, nsURI, doc)  
      CType(doc, LineInfoDocument).IncrementElementCount()  
   End Sub 'New  
  
   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)  
      lineNumber = linenum  
      linePosition = linepos  
   End Sub 'SetLineInfo  
  
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
   End Function 'HasLineInfo  
End Class 'LineInfoElement ' End LineInfoElement class.  
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
 Následující příklad vrátí počet prvků v dokumentu XML.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.IO  
  
 _  
  
Class LineInfoDocument  
   Inherits XmlDocument  
  
   Private elementCount As Integer  
  
   Friend Sub New()  
      elementCount = 0  
   End Sub 'New  
  
   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement  
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)  
      Return elem  
   End Function 'CreateElement  
  
   Public Sub IncrementElementCount()  
      elementCount += 1  
   End Sub 'IncrementElementCount  
  
   Public Function GetCount() As Integer  
      Return elementCount  
   End Function 'GetCount  
End Class 'LineInfoDocument  
 _ 'End LineInfoDocument class.  
  
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
   End Sub 'Main   
End Class 'Test  
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
  
##### <a name="input"></a>Vstup  
 Book.XML  
  
```xml  
<!--sample XML fragment-->  
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>  
  <title>The Handmaid's Tale</title>  
  <price>14.95</price>  
</book>  
```  
  
##### <a name="output"></a>Výstup  
  
```  
Number of elements in book.xml: 3  
```  
  
 Příkladem zobrazujícím postup rozšíření třídy XML DOM (System.Xml) najdete v www.gotdotnet.com/userfiles/XMLDom/extendDOM.zip.  
  
## <a name="node-event-handler"></a>Obslužné rutiny události uzlu  
 Implementace rozhraní .NET Framework modelu DOM také zahrnuje systém události, který vám umožní přijímat a zpracovávat události při změně uzly v dokumentu XML. Pomocí <xref:System.Xml.XmlNodeChangedEventHandler> a <xref:System.Xml.XmlNodeChangedEventArgs> třídy, můžete zaznamenávat `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, a `NodeRemoving` události.  
  
 Zpracování událostí proces funguje stejně v odvozených třídách stejně jako v původní DOM třídy.  
  
 Další informace týkající se zpracování událostí uzlu najdete v tématu [události](../../../../docs/standard/events/index.md) a <xref:System.Xml.XmlNodeChangedEventHandler>.  
  
## <a name="default-attributes-and-the-createelement-method"></a>Výchozí atributy a metoda CreateElement  
 Pokud přepíšete <xref:System.Xml.XmlDocument.CreateElement%2A> metoda v odvozené třídě, výchozí atributy nepřidávají při vytváření nové prvky při úpravách dokumentu. Jedná se pouze o problém při úpravách. Protože <xref:System.Xml.XmlDocument.CreateElement%2A> metoda je zodpovědný za přidání výchozí atributy, které mají <xref:System.Xml.XmlDocument>, musí code tuto funkci v <xref:System.Xml.XmlDocument.CreateElement%2A> metoda. Při zavádění <xref:System.Xml.XmlDocument> , který obsahuje výchozí atributy, se budou zpracovávat správně. Další informace o výchozí atributy najdete v tématu [vytváření nové atributy pro elementy v modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
