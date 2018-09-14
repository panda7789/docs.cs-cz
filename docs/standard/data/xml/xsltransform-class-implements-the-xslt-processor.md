---
title: Třída XslTransform implementuje procesor XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81d0ce4f697935908b8ad7084560bd1adacbdf2d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519614"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>Třída XslTransform implementuje procesor XSLT
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.Xsl.XslTransform> Třída je procesor XSLT implementaci transformace XSL (XSLT) verze 1.0 doporučení. <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda vyhledá a načte šablony stylů a <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda transformuje daném zdrojovém dokumentu. Jakékoli úložiště, který implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní lze použít jako zdrojový dokument pro <xref:System.Xml.Xsl.XslTransform>. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Aktuálně implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>, takže všechny z nich může sloužit jako vstupní zdrojový dokument k transformaci.  
  
 <xref:System.Xml.Xsl.XslTransform> Objekt [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podporuje pouze specifikaci XSLT 1.0, definované pomocí následující obor názvů:  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 Šablony stylů můžete načíst pomocí <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda z jednoho z následujících tříd:  
  
-   XPathNavigator  
  
-   Objekt XmlReader  
  
-   Řetězec představující adresu URL  
  
 Existuje jiný <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda pro každou z výše uvedených vstupní tříd. Některé metody trvat, než se kombinace jedné z těchto tříd a <xref:System.Xml.XmlResolver> třídu jako argumenty. <xref:System.Xml.XmlResolver> Vyhledává prostředky odkazuje `<xsl:import>` nebo `<xsl:include>` najít v šabloně stylů. Následující metody přijímají řetězce, <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> jako vstup.  
  
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
  
 Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> metody uvedené nahoře využijte <xref:System.Xml.XmlResolver> jako parametr. <xref:System.Xml.XmlResolver> Slouží k načtení šablony stylů a všechny seznamy stylu odkazuje XSL: Import a xsl: zahrnout elementy.  
  
 Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> taky využít důkazy jako parametr metody. Parametr důkazy je <xref:System.Security.Policy.Evidence> přidružený k šabloně stylů. Úroveň zabezpečení šablony stylů má vliv na následné prostředků, odkazuje na úroveň zabezpečení, jako je například skript obsahuje, všechny `document()` funkce používá a všechny objekty, rozšíření používané <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Pokud je načten pomocí šablony stylů <xref:System.Xml.Xsl.XslTransform.Load%2A> poskytuje metodu, která obsahuje parametr adresy URL a žádné legitimaci, díky kombinaci dané adrese URL s jeho lokality a zóny se počítá doklad o šablony stylů.  
  
 Pokud je k dispozici žádný identifikátor URI nebo doklad, důkazy pro šablony stylů je plně důvěryhodné. Načtení šablony stylů z nedůvěryhodných zdrojů, ani přidat objekty nedůvěryhodné rozšíření do <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Další informace o úrovně zabezpečení a důkazy a o jejím dopadu skriptování najdete v tématu [pomocí skriptování šablony stylů XSLT \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Informace o úrovně zabezpečení a důkazy a o jejím dopadu objektů rozšíření najdete v tématu [třída XsltArgumentList pro parametry list stylu a objektů rozšíření](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).  
  
 Informace o úrovně zabezpečení a důkazy a o jejím dopadu `document()` funkce naleznete v tématu [překlad externích šablon stylů XSLT a dokumenty](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).  
  
 Šablona stylů můžete zadat s počtem vstupních parametrů. Funkce šablony stylů můžete také volat u objektů rozšíření. Parametry a objektů rozšíření jsou dodávány pomocí list stylu <xref:System.Xml.Xsl.XsltArgumentList> třídy. Další informace o <xref:System.Xml.Xsl.XsltArgumentList>, naleznete v tématu <xref:System.Xml.Xsl.XsltArgumentList>.  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a>Doporučené zabezpečení použití třídy XslTransform  
 Oprávnění zabezpečení šablony stylů, závisí na důkazy, které jsou k dispozici. Následující tabulka shrnuje umístění šablony stylů a poskytuje vysvětlení, co typu legitimací poskytnout.  
  
-   Šablony stylů XSLT nemá žádné externí odkazy nebo šablony stylů pochází ze základu kódu, které důvěřujete.  
  
    -   Poskytnout důkazy z vašeho sestavení:  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   Šablony stylů XSLT pochází z vnějšího zdroje. Označuje původu zdroje a není ověřitelný identifikátoru URI.  
  
    -   Vytvoření důkazy použitím tohoto identifikátoru URI.  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   Šablony stylů XSLT pochází z vnějšího zdroje. Původní zdroj není známý.  
  
    -   Nastavte na důkaz `null`. Bloky kódu skriptu nejsou zpracovány, XSLT `document()` funkce není podporována a objektů privilegovaných rozšíření jsou zakázána.  
  
         Kromě toho můžete také nastavit `resolver` parametr `null` to zajistí, že `xsl:import` a `xsl:include` nejsou zpracovávány elementy.  
  
-   Šablony stylů XSLT pochází z vnějšího zdroje. Původní zdroj není znám, ale budete potřebovat podporu skriptu.  
  
    -   Žádost o legitimaci od volajícího.  
  
## <a name="transformation-of-xml-data"></a>Transformaci dat XML  
 Po načtení šablony stylů transformace začíná voláním jedné z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody a poskytnutí vstupní zdrojový dokument. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Je přetížena metoda poskytnout různé transformace výstupy. Transformace může mít za následek následující formáty výstupu:  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   Adresa URL řetězec souboru  
  
 Tento poslední formát URL řetězec poskytuje běžně používané scénáři transformují vstupní dokument nachází v adrese URL a zápis dokumentu do výstupní adresy URL. To <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je metoda pohodlí k načítání dokumentu XML ze souboru, provedení transformace XSLT a zapisovat výstup do souboru. To zabrání by bylo nutné vytvořit a načíst vstupní zdrojový dokument a pak zápis do datového proudu souboru. Následující příklad kódu ukazuje toto použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu pomocí adresy URL řetězec jako vstup a výstup:  
  
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
  
## <a name="transforming-a-section-of-an-xml-document"></a>Transformace část dokumentu XML  
 Transformace se vztahují k dokumentu jako celek. Jinými slovy Pokud předáte v uzlu, než je kořenový uzel dokumentu, toto nezabraňuje proces transformace přístup na všechny uzly v načtený dokument. K transformaci fragment stromu výsledek, musíte vytvořit <xref:System.Xml.XmlDocument> obsahující stromu výsledek fragment a předat ho <xref:System.Xml.XmlDocument> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda. Následující příklad provede transformaci fragment stromu výsledek.  
  
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
  
 V příkladu se používá library.xml print_root.xsl soubory a jako vstup a vrátí tento výstup do konzoly.  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 Library.XML  
  
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
  
 print_root.xsl  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>Migrace XSLT v rozhraní .NET Framework verze 1.0 rozhraní .NET Framework verze 1.1  
 V následující tabulce jsou uvedeny zastaralý [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.0 a nové [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.1 <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda. Nové metody umožňují omezit oprávnění šablony stylů zadáním důkaz.  
  
|Zastaralé metod rozhraní .NET Framework verze 1.0 zatížení|Náhradní rozhraní .NET Framework verze 1.1 zatížení metody|  
|------------------------------------------------------|---------------------------------------------------------|  
|Načtení (objektem XPathNavigator nastaveným na vstupu);<br /><br /> Load (objektem XPathNavigator nastaveným na vstupu, objekt XmlResolver překladač);|Zatížení (Šablona stylů objektem XPathNavigator nastaveným na, objekt XmlResolver překladače, důkazy důkazy);|  
|Zatížení (Šablona stylů IXPathNavigable);<br /><br /> Zatížení (Šablona stylů IXPathNavigable, objekt XmlResolver překladač);|Zatížení (Šablona stylů IXPathNavigable, objekt XmlResolver překladače, důkazy důkazy);|  
|Zatížení (Šablona stylů XmlReader);<br /><br /> Zatížení (Šablona stylů XmlReader, objekt XmlResolver překladač);|Zatížení (Šablona stylů XmlReader, objekt XmlResolver překladač, důkazy důkazy);|  
  
 V následující tabulce jsou uvedeny zastaralé a nové metody pro <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody. Využijte nové metody <xref:System.Xml.XmlResolver> objektu.  
  
|Zastaralé metody transformace rozhraní .NET Framework verze 1.0|Nahrazení verzi rozhraní .NET Framework 1.1 metody transformace|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|Objekt XmlReader Transform(XPathNavigator input, XsltArgumentList args)|Objekt XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)|  
|Objekt XmlReader Transform(IXPathNavigable input, XsltArgumentList args)|Objekt XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)|  
|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, XmlWriter výstup)|Void transformace (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstup XmlWriter, objekt XmlResolver překladač)|  
|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, XmlWriter výstup)|Transformace void (IXpathNavigable vstup, třída XsltArgumentList argumentů, výstup XmlWriter, objekt XmlResolver překladač)|  
|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, TextWriter výstup)|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, TextWriter výstup, objekt XmlResolver překladač)|  
|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, TextWriter výstup)|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, TextWriter výstup, objekt XmlResolver překladač)|  
|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, Stream výstup)|Void transformace (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstupní Stream, objekt XmlResolver překladač)|  
|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, Stream výstup)|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, výstupní Stream, objekt XmlResolver překladač)|  
|Zrušit transformaci (řetězec vstupní, výstupní řetězec);|Zrušit transformaci (řetězec vstupní, výstupní řetězec, objekt XmlResolver překladač);|  
  
 <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Vlastnost je zastaralá v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1. Místo toho použijte nové <xref:System.Xml.Xsl.XslTransform.Transform%2A> přetížení, která berou <xref:System.Xml.XmlResolver> objektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslTransform>  
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
