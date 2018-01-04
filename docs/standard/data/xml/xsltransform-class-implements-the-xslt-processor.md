---
title: "Třída XslTransform implementuje procesoru XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f1367268920e4b72f29b77a7f2e96f09a1dce37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>Třída XslTransform implementuje procesoru XSLT
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.Xsl.XslTransform> Třída je procesor XSLT implementace doporučení XSL transformace XSLT () verze 1.0. <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda vyhledá a načte šablony stylů a <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda transformuje dané zdrojový dokument. Jakékoli úložiště, který implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní lze použít jako zdroj dokumentu <xref:System.Xml.Xsl.XslTransform>. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Aktuálně implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>, takže všechny tyto lze použít jako vstupní zdroj dokumentu, který má transformace.  
  
 <xref:System.Xml.Xsl.XslTransform> Objekt v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podporuje pouze specifikaci XSLT 1.0, definovanou s následujícím oborem názvů:  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 Šablony stylů mohou být načteny, pomocí <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda z jednoho z následujících tříd:  
  
-   Objektem XPathNavigator nastaveným na  
  
-   XmlReader  
  
-   Řetězec představující adresu URL  
  
 Existuje jiné <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda pro každou z výše uvedených vstupní tříd. Některé metody proveďte jednu z těchto tříd kombinace a <xref:System.Xml.XmlResolver> třída jako argumenty. <xref:System.Xml.XmlResolver> Vyhledá prostředky odkazuje `<xsl:import>` nebo `<xsl:include>` najít v šabloně stylů. Tyto metody přijímají řetězce <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> jako vstup.  
  
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
  
 Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> metody uvedené výše proveďte <xref:System.Xml.XmlResolver> jako parametr. <xref:System.Xml.XmlResolver> Slouží k načtení šablony stylů a všechny styl listy, kterou se odkazuje v xsl:import a xsl: zahrnují elementy.  
  
 Většina <xref:System.Xml.Xsl.XslTransform.Load%2A> metody také přijímají důkaz jako parametr. Je parametr důkaz <xref:System.Security.Policy.Evidence> je spojeno s šablony stylů. Úroveň zabezpečení šablony stylů ovlivňuje všechny následné prostředky odkazuje na úroveň zabezpečení, jako je například skript obsahuje, všechny `document()` používá funkce a všechny objekty rozšíření používané <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Pokud je načten pomocí šablony stylů <xref:System.Xml.Xsl.XslTransform.Load%2A> poskytuje metodu, která obsahuje parametr adresy URL a žádné důkaz, důkaz šablony stylů se počítá kombinací dané adrese URL s jeho lokality a zóny.  
  
 Pokud je zadaný žádný identifikátor URI nebo důkaz, je důkaz nastavení pro šablony stylů plně důvěryhodný. Nezadávejte načtení šablony stylů z nedůvěryhodných zdrojů nebo přidat objekty nedůvěryhodné rozšíření do <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Další informace o úrovně zabezpečení a důkaz a jak ovlivňuje skriptování najdete v tématu [XSLT skriptování pomocí šablony stylů \<msxsl:script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Informace o úrovně zabezpečení a důkaz a jak ovlivňuje objektů rozšíření najdete v tématu [třída XsltArgumentList pro parametry list stylu a rozšíření objekty](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).  
  
 Informace o úrovně zabezpečení a důkaz a jak ovlivňuje `document()` funkce najdete v tématu [řešení externí XSLT šablony stylů a dokumenty](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).  
  
 Šablony stylů můžete zadat s počtem vstupní parametry. Funkce pro objekty rozšíření můžete také volat šablony stylů. Parametry a objektů rozšíření jsou zadaná na list stylu pomocí <xref:System.Xml.Xsl.XsltArgumentList> třídy. Další informace o <xref:System.Xml.Xsl.XsltArgumentList>, najdete v části <xref:System.Xml.Xsl.XsltArgumentList>.  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a>Doporučené zabezpečení použití XslTransform – třída  
 Oprávnění zabezpečení šablony stylů závisí na důkaz zadat. Následující tabulka shrnuje umístění šablony stylů a vysvětluje, co typu důkaz poskytnout.  
  
-   Styl XSLT nemá žádné externí odkazy nebo šablony stylů pochází od základu kódu, které důvěřujete.  
  
    -   Prokázání vaší sestavení:  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   Styl XSLT pochází z vnějšího zdroje. Je známý původ zdroje a je ověřitelná identifikátoru URI.  
  
    -   Vytvořte důkaz pomocí identifikátoru URI.  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   Styl XSLT pochází z vnějšího zdroje. Původ zdroje není znám.  
  
    -   Nastavte na důkaz `null`. Bloky Script nebudou zpracovány, XSLT `document()` funkce není podporována a objektů privilegované rozšíření nejsou povoleny.  
  
         Kromě toho můžete také nastavit `resolver` parametru `null` to zajistí, že `xsl:import` a `xsl:include` elementy nejsou předmětem zpracování.  
  
-   Styl XSLT pochází z vnějšího zdroje. Původ zdroje není znám, ale budete potřebovat podporu skriptu.  
  
    -   Požadovat doklad volající.  
  
## <a name="transformation-of-xml-data"></a>Transformace dat XML  
 Po načtení šablony stylů transformace začne volání jedné z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody a poskytnutí dokument vstupní zdroj. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda je přetížena zajistit výstupy různých transformace. Transformace může mít za následek následující formáty výstup:  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   Adresa URL řetězec souboru  
  
 Tento poslední formát adresu URL řetězec poskytuje běžně používané scénáři transformace vstupní dokument umístěný v adrese URL a zápis dokumentu na adresu URL výstup. To <xref:System.Xml.Xsl.XslTransform.Transform%2A> je užitečný způsob k načítání dokumentu XML ze souboru, provést transformace XSLT a zapisovat výstup do souboru. To zabrání nutnosti vytvoření a načtení dokumentu vstupní zdroj a pak zápis do datového proudu souboru. Následující příklad kódu ukazuje, toto využití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda pomocí adresy URL řetězec jako vstup a výstup:  
  
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
  
## <a name="transforming-a-section-of-an-xml-document"></a>Transformace části dokumentu XML  
 Transformace se vztahují k dokumentu jako celku. Jinými slovy Pokud předáte v uzlu než kořenový uzel dokumentu, toto nezabrání proces transformace přístup na všechny uzly v načíst dokumentu. K transformaci fragment výsledek stromu, musíte vytvořit <xref:System.Xml.XmlDocument> obsahující jenom stromu výsledek fragmentovat a předejte který <xref:System.Xml.XmlDocument> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda. Následující příklad provádí transformaci fragment stromu výsledek.  
  
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
  
 V příkladu se používá library.xml a print_root.xsl soubory jako vstupy a výstupy následující ke konzole.  
  
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
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>Migrace XSLT z rozhraní .NET Framework verze 1.0 pro rozhraní .NET Framework verze 1.1  
 V následující tabulce jsou uvedeny zastaralé [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.0 a nové [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody verze 1.1 <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda. Nové metody umožňují omezit oprávnění šablony stylů zadáním důkaz.  
  
|Zastaralé metody zatížení rozhraní .NET Framework verze 1.0|Nahrazení rozhraní .NET Framework verze 1.1 zatížení metody|  
|------------------------------------------------------|---------------------------------------------------------|  
|Načíst (objektem XPathNavigator nastaveným na vstup);<br /><br /> Zatížení (objektem XPathNavigator nastaveným na vstupu, objekt XmlResolver překladač);|Zatížení (objektem XPathNavigator nastaveným na šablony stylů, objekt XmlResolver překladač důkaz důkaz);|  
|Načíst (IXPathNavigable šablony stylů);<br /><br /> Zatížení (IXPathNavigable stylů, objekt XmlResolver překladač);|Zatížení (IXPathNavigable stylů, objekt XmlResolver překladač důkaz důkaz);|  
|Načíst (XmlReader šablony stylů);<br /><br /> Zatížení (XmlReader stylů, objekt XmlResolver překladač);|Zatížení (XmlReader stylů, objekt XmlResolver překladač důkaz důkaz);|  
  
 V následující tabulce jsou zastaralé a nové metody pro <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda. Nové metody přijímají <xref:System.Xml.XmlResolver> objektu.  
  
|Zastaralé metody transformace rozhraní .NET Framework verze 1.0|Nahrazení rozhraní .NET Framework verze 1.1 metody transformace|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|XmlReader Transform(XPathNavigator input, XsltArgumentList args)|XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)|  
|XmlReader Transform(IXPathNavigable input, XsltArgumentList args)|XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)|  
|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, XmlWriter výstup)|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, XmlWriter výstup, objekt XmlResolver překladač)|  
|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, XmlWriter výstup)|Transformace void (IXpathNavigable vstup, třída XsltArgumentList argumentů, XmlWriter výstup, objekt XmlResolver překladač)|  
|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů výstup TextWriter.)|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstup TextWriter, objekt XmlResolver překladač)|  
|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů výstup TextWriter.)|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, výstup TextWriter, objekt XmlResolver překladač)|  
|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů výstup datového proudu.)|Transformace void (objektem XPathNavigator nastaveným na vstup, třída XsltArgumentList argumentů, výstup datového proudu, objekt XmlResolver překladač)|  
|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů výstup datového proudu.)|Transformace void (IXPathNavigable vstup, třída XsltArgumentList argumentů, výstup datového proudu, objekt XmlResolver překladač)|  
|Void transformace (řetězec vstupní, výstupní řetězec);|Void transformace (řetězec vstupní, výstupní řetězec, objekt XmlResolver překladač);|  
  
 <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Vlastnost je zastaralá ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.1. Místo toho použít novou <xref:System.Xml.Xsl.XslTransform.Transform%2A> přetížení, která berou <xref:System.Xml.XmlResolver> objektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Xsl.XslTransform>  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
