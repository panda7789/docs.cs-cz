---
title: Třída XslTransform implementuje procesor XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
ms.openlocfilehash: 73a432db9a3fcb6587184e27e6dfe9ba49010e92
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709605"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>Třída XslTransform implementuje procesor XSLT

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .

<xref:System.Xml.Xsl.XslTransform> Třída je procesor XSLT implementující doporučení XSL transformace (XSLT) verze 1,0. <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda vyhledá a přečte šablony stylů a <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda transformuje daný zdrojový dokument. Jakékoli úložiště, které implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, lze použít jako zdrojový dokument pro <xref:System.Xml.Xsl.XslTransform>. <xref:System.Xml.XPath.IXPathNavigable> .NET Framework aktuálně implementuje rozhraní <xref:System.Xml.XmlDocument>na, <xref:System.Xml.XmlDataDocument>a, a <xref:System.Xml.XPath.XPathDocument>, takže všechny z nich lze použít jako vstupní zdrojový dokument pro transformaci.

<xref:System.Xml.Xsl.XslTransform> Objekt v .NET Framework podporuje pouze specifikaci XSLT 1,0, která je definována s následujícím oborem názvů:

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

Šablonu stylů lze načíst pomocí <xref:System.Xml.Xsl.XslTransform.Load%2A> metody z jedné z následujících tříd:

- Objekt

- Objekt

- Řetězec představující adresu URL

Každá z výše uvedených <xref:System.Xml.Xsl.XslTransform.Load%2A> tříd input má jinou metodu. Některé metody přebírají kombinaci jedné z těchto tříd a <xref:System.Xml.XmlResolver> třídy jako argumenty. <xref:System.Xml.XmlResolver> Vyhledá prostředky, na které `<xsl:import>` odkazuje `<xsl:include>` nebo který najdete v šabloně stylů. Následující metody pobírají řetězec, <xref:System.Xml.XmlReader>nebo <xref:System.Xml.XPath.XPathNavigator> jako vstup.

```vb
Overloads Public Sub Load(String)
```

```csharp
public void Load(string);
```

```vb
Overloads Public Sub Load(String, XmlResolver)
```

```csharp
public void Load(string, XmlResolver);
```

```vb
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)
```

```csharp
public void Load(XmlReader, XmlResolver, Evidence);
```

```vb
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)
```

```csharp
public void Load(XPathNavigator, XmlResolver, Evidence);
```

Většina výše uvedených <xref:System.Xml.Xsl.XslTransform.Load%2A> metod vezme <xref:System.Xml.XmlResolver> jako parametr. Slouží <xref:System.Xml.XmlResolver> k načtení šablony stylů a všech šablon stylů, na které se odkazuje v elementech xsl: Import a xsl: include.

Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> metod také převezme legitimaci jako parametr. Parametr legitimace je <xref:System.Security.Policy.Evidence> přidružený k šabloně stylů. Úroveň zabezpečení šablon stylů má vliv na úroveň zabezpečení všech dalších prostředků, na které odkazuje, jako je například skript, který obsahuje, všechny `document()` funkce, které používá, a všechny objekty rozšíření používané <xref:System.Xml.Xsl.XsltArgumentList>.

Pokud je šablona stylů načtena pomocí <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, která obsahuje parametr adresy URL a není zadán žádný důkaz, legitimace v šabloně stylů se vypočítá kombinací dané adresy URL k jejímu webu a zóně.

Pokud nejsou zadány žádné identifikátory URI ani legitimace, pak je sada legitimace pro šablonu stylů plně důvěryhodná. Nečtěte šablony stylů z nedůvěryhodných zdrojů nebo přidejte nedůvěryhodné objekty rozšíření do <xref:System.Xml.Xsl.XsltArgumentList>.

Další informace o úrovních a důkazech zabezpečení a o tom, jak ovlivňují skriptování, najdete v tématu [skriptování XSLT XSL pomocí \<msxsl: Script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Informace o úrovních zabezpečení a legitimaci a o tom, jak ovlivňují objekty rozšíření, naleznete v tématu [třída XsltArgumentList pro parametry a objekty rozšíření šablon stylů](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).

Informace o úrovních zabezpečení a legitimaci a jejich vlivu na `document()` funkci naleznete v tématu [řešení externích šablon stylů XSLT a dokumentů](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).

Šablonu stylů lze zadat s počtem vstupních parametrů. Šablona stylů může také volat funkce objektů rozšíření. Parametry a objekty rozšíření jsou dodány do předlohy stylů pomocí <xref:System.Xml.Xsl.XsltArgumentList> třídy. Další informace o <xref:System.Xml.Xsl.XsltArgumentList>naleznete v tématu <xref:System.Xml.Xsl.XsltArgumentList>.

## <a name="recommended-secure-use-of-xsltransform-class"></a>Doporučené zabezpečené použití třídy XslTransform

Oprávnění zabezpečení pro šablonu stylů závisí na poskytnutých důkazech. Následující tabulka shrnuje umístění předlohy se styly a poskytuje vysvětlení, jaký typ legitimace má poskytnout.

- Šablona stylů XSLT neobsahuje žádné externí odkazy nebo šablona stylů pochází ze základu kódu, kterému důvěřujete.

  - Zadejte legitimaci ze sestavení:

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- Šablona stylů XSLT pochází z vnějšího zdroje. Původ zdroje je známý a existuje ověřitelný identifikátor URI.

  - Vytvořte legitimaci pomocí identifikátoru URI.

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- Šablona stylů XSLT pochází z vnějšího zdroje. Původ zdroje není známý.

  - Nastavte legitimaci `null`na. Bloky skriptu nejsou zpracovány, funkce XSLT `document()` není podporována a objekty privilegovaného rozšíření nejsou povoleny.

    Kromě toho můžete také `resolver` nastavit parametr tak, aby `null` se zajistilo `xsl:import` , `xsl:include` že a prvky nebudou zpracovány.

- Šablona stylů XSLT pochází z vnějšího zdroje. Původ zdroje není známý, ale vyžadujete podporu skriptů.

  - Požaduje se legitimace od volajícího.

## <a name="transformation-of-xml-data"></a>Transformace dat XML

Po načtení šablon stylů se transformace spustí voláním jedné z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metod a zadáním vstupního zdrojového dokumentu. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda je přetížena, aby poskytovala různé výstupy transformace. Transformace může mít za následek následující formáty výstupu:

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- Adresa URL řetězce souboru

V tomto posledním formátu adresa URL řetězce poskytuje často používaný scénář pro transformaci vstupního dokumentu umístěného v adrese URL a zápis dokumentu do výstupní adresy URL. Tato <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je pohodlnější způsob, jak načíst dokument XML ze souboru, provést transformaci XSLT a zapsat výstup do souboru. Tím zabráníte tomu, abyste vytvořili a načetli vstupní zdrojový dokument a potom zapsali do datového proudu souboru. Následující ukázka kódu ukazuje toto použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody pomocí adresy URL řetězce jako vstupu a výstupu:

```vb
Dim xsltransform As XslTransform = New XslTransform()
xsltransform.Load("favorite.xsl")
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)
```

```csharp
XslTransform xsltransform = new XslTransform();
xsltransform.Load("favorite.xsl");
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);
```

## <a name="transforming-a-section-of-an-xml-document"></a>Transformace oddílu dokumentu XML

Transformace se vztahují na dokument jako celek. Jinými slovy, Pokud předáte v jiném než kořenovém uzlu dokumentu, nezabrání to procesu transformace v přístupu ke všem uzlům v načteném dokumentu. Chcete-li transformovat fragment stromu výsledek, je nutné <xref:System.Xml.XmlDocument> vytvořit objekt obsahující pouze fragment stromu výsledek a předat <xref:System.Xml.XmlDocument> ho <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodě. Následující příklad provede transformaci fragmentu stromu výsledek.

```vb
Dim xslt As New XslTransform()
xslt.Load("print_root.xsl")
Dim doc As New XmlDocument()
doc.Load("library.xml")
' Create a new document containing just the result tree fragment.
Dim testNode As XmlNode = doc.DocumentElement.FirstChild
Dim tmpDoc As New XmlDocument()
tmpDoc.LoadXml(testNode.OuterXml)
' Pass the document containing the result tree fragment
' to the Transform method.
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)
```

```csharp
XslTransform xslt = new XslTransform();
xslt.Load("print_root.xsl");
XmlDocument doc = new XmlDocument();
doc.Load("library.xml");
// Create a new document containing just the result tree fragment.
XmlNode testNode = doc.DocumentElement.FirstChild;
XmlDocument tmpDoc = new XmlDocument();
tmpDoc.LoadXml(testNode.OuterXml);
// Pass the document containing the result tree fragment
// to the Transform method.
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");
xslt.Transform(tmpDoc, null, Console.Out, null);
```

V příkladu se jako vstup používá soubor Library. XML a print_root. XSL a v konzole se vytvoří výstup následujícího:

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

Library. XML

```xml
<library>
  <book genre='novel' ISBN='1-861001-57-5'>
     <title>Pride And Prejudice</title>
  </book>
  <book genre='novel' ISBN='1-81920-21-2'>
     <title>Hook</title>
  </book>
</library>
```

print_root. xsl

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>Migrace XSLT z verze .NET Framework 1,0 na .NET Framework verze 1,1

Následující tabulka uvádí zastaralé metody verze 1,0 .NET Framework a nové metody .NET Framework verze 1,1 pro <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu. Nové metody umožňují omezit oprávnění k šabloně stylů zadáním legitimace.

|Zastaralé metody Load .NET Framework verze 1,0|Nahrazení metod Load .NET Framework verze 1,1|
|------------------------------------------------------|---------------------------------------------------------|
|Load (vstup XPathNavigator);<br /><br /> Load (vstup XPathNavigator, překladač objekt XmlResolver);|Load (šablona XPathNavigator, překladač objekt XmlResolver, legitimace legitimace);|
|Načíst (IXPathNavigable StyleSheet);<br /><br /> Load (IXPathNavigable StyleSheet; objekt XmlResolver resolver);|Load (šablona stylů IXPathNavigable, překladač objekt XmlResolver, legitimace legitimace);|
|Načíst (předloha XmlReader);<br /><br /> Load (šablona XmlReader, překladač objekt XmlResolver);|Load (šablona XmlReader, překladač objekt XmlResolver, legitimace legitimace);|

V následující tabulce jsou uvedeny zastaralé a nové metody pro <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu. Nové metody přebírají <xref:System.Xml.XmlResolver> objekt.

|Zastaralé metody transformace verze 1,0 .NET Framework|Náhrada .NET Framework metod transformace verze 1,1|
|-----------------------------------------------------------|--------------------------------------------------------------|
|XmlReader Transform (vstup XPathNavigator, třída XsltArgumentList args)|XmlReader Transform (Input XPathNavigator, třída XsltArgumentList args, překladač objekt XmlResolver)|
|Transformace XmlReader (IXPathNavigable Input, třída XsltArgumentList args)|Transformace XmlReader (IXPathNavigable Input, třída XsltArgumentList args, překladač objekt XmlResolver)|
|Void – transformace (vstup XPathNavigator, argumenty třída XsltArgumentList, výstup XmlWriter)|Void – transformace (vstup XPathNavigator, argumenty třída XsltArgumentList, výstup XmlWriter, překladač objekt XmlResolver)|
|Void Transform (IXPathNavigable Input, třída XsltArgumentList args, XmlWriter Output)|Void Transform (IXpathNavigable Input, třída XsltArgumentList args, XmlWriter Output, překladač objekt XmlResolver)|
|Void – transformace (vstup XPathNavigator, třída XsltArgumentList argumenty, TextWriter výstup)|Void – transformace (vstup XPathNavigator, třída XsltArgumentList args, TextWriter Output, překladač objekt XmlResolver)|
|Void Transform (IXPathNavigable Input, třída XsltArgumentList args, TextWriter Output)|Void Transform (IXPathNavigable Input, třída XsltArgumentList args, TextWriter Output, překladač objekt XmlResolver)|
|Void – transformace (vstup XPathNavigator, třída XsltArgumentList argumenty, výstup datového proudu)|Void – transformace (vstup XPathNavigator, třída XsltArgumentList argumenty, výstup datového proudu, překladač objekt XmlResolver)|
|Void Transform (vstup IXPathNavigable, argumenty třída XsltArgumentList, výstup datového proudu)|Void Transform (vstup IXPathNavigable, třída XsltArgumentList argumenty, výstup datového proudu, překladač objekt XmlResolver)|
|Void – transformace (vstup řetězce, výstup řetězce);|Void – transformace (vstup řetězce, výstup řetězce, překladač objekt XmlResolver);|

Tato <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> vlastnost je zastaralá ve verzi .NET Framework 1,1. Místo toho použijte nová <xref:System.Xml.Xsl.XslTransform.Transform%2A> přetížení, která přijímají <xref:System.Xml.XmlResolver> objekt.

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Xsl.XslTransform>
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
