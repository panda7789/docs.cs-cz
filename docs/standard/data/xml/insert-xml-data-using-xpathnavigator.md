---
title: "Vkládání dat XML pomocí objektem XPathNavigator nastaveným na"
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
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34151590a14c48c0a84677f2d7cae662291edf40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Vkládání dat XML pomocí objektem XPathNavigator nastaveným na
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, používá se k vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML. Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, který je jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator>objekty, které můžete upravit dokument XML, které jsou vytvořené pomocí <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a jakýkoli pokus o úpravu metody použijte <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený <xref:System.Xml.XPath.XPathDocument> objekt výsledkem <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete v části [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Vkládání uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody pro vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML. Tyto metody umožňují vložit uzly a atributy v různých umístěních ve vztahu k aktuální pozici <xref:System.Xml.XPath.XPathNavigator> objektu a jsou popsané v následujících částech.  
  
### <a name="inserting-sibling-nodes"></a>Vkládání uzly na stejné úrovni  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, které vložit uzly na stejné úrovni.  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Tyto metody vložit na stejné úrovni jako uzly před a za uzel <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody jsou přetížené a přijmout `string`, <xref:System.Xml.XmlReader> objekt, nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje uzel na stejné úrovni, který chcete přidat jako parametry. Obě metody se taky vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení uzly na stejné úrovni.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody vložení na stejné úrovni jako jednoho uzlu před a po uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na pomocí předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.  
  
 V následujícím příkladu a nové `pages` element je vložen před `price` první podřízený prvek `book` element v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody, najdete v článku <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci k nástroji.  
  
### <a name="inserting-child-nodes"></a>Vkládání podřízené uzly  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, které vložit podřízené uzly.  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Tyto metody připojit a předřazení podřízených uzlů na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.  
  
 Metody v části "Vkládání uzly na stejné úrovni", jako <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody přijímají `string`, <xref:System.Xml.XmlReader> objekt, nebo <xref:System.Xml.XPath.XPathNavigator> objekt obsahující podřízený uzel, který chcete přidat jako parametry. Obě metody se taky vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení podřízené uzly.  
  
 Také jako metody v části "Vkládání uzly na stejné úrovni" <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody vložit jeden podřízený uzel na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na pomocí Předpona oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.  
  
 V následujícím příkladu nový `pages` připojí se k seznamu podřízených elementů první podřízený element `book` element v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody, najdete v článku <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci k nástroji.  
  
### <a name="inserting-attribute-nodes"></a>Vkládání atribut uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, které vložit atribut uzlů.  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Tyto metody vložit atribut uzly na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda vytvoří uzlu atributu na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na pomocí předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda vrátí <xref:System.Xml.XmlWriter> objekt použitý k vložení atribut uzlů.  
  
 V následujícím příkladu, nové `discount` a `currency` atributy se vytvářejí na `price` první podřízený prvek `book` element v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XmlWriter> objekt vrácený <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody, najdete v článku <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci k nástroji.  
  
## <a name="copying-nodes"></a>Kopírování uzly  
 V některých případech můžete chtít naplnit dokumentu XML se obsah z jiného dokumentu XML. Obě <xref:System.Xml.XPath.XPathNavigator> – třída a <xref:System.Xml.XmlWriter> třídy můžete zkopírovat uzly, aby <xref:System.Xml.XmlDocument> objekt z existující <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objektu.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody <xref:System.Xml.XPath.XPathNavigator> třída všechny mají přetížení, které může přijmout <xref:System.Xml.XPath.XPathNavigator> objekt nebo <xref:System.Xml.XmlReader> objekt jako parametr.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> Metodu <xref:System.Xml.XmlWriter> třída má přetížení, která může přijmout <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> objektu.  
  
 Následující příklad zkopíruje všechny `book` elementy z jednoho dokumentu do jiného.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a>Vložení hodnoty  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody vložit hodnoty pro uzel do <xref:System.Xml.XmlDocument> objektu.  
  
### <a name="inserting-untyped-values"></a>Vkládání bez typu hodnoty  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnota předaná jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na. Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud je k dispozici informace o schématu.  
  
 V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` elementů v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Vkládání zadávaných hodnot  
 Pokud je typ uzlu schématu XML W3C jednoduchý typ, nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda bude zkontrolován omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavená. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnotu `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem výjimka.  
  
 V následujícím příkladu se pokusí změnit hodnotu `price` element první `book` element v `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu. Vzhledem k tomu, že typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` soubory, to vede k výjimce.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad také trvá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml a OuterXml vlastnosti  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třída změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na s Analyzovaná obsah daného XML `string`. Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na i aktuální uzel.  
  
 Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti slouží k vložení uzlů a hodnoty v dokumentu XML. Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti, které chcete vložit uzly a hodnoty, najdete v článku [upravit Data XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace XML: lang konflikty a  
 Některé konflikty související do oboru názvů a `xml:lang` deklarace může dojít při vkládání dat XML pomocí <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídu, která trvat <xref:System.Xml.XmlReader>objektů jako parametry.  
  
 Níže jsou uvedeny možné obor názvů konfliktů.  
  
-   Pokud dojde oboru názvů v oboru v rámci <xref:System.Xml.XmlReader> objektu kontextu, kde předponu pro obor názvů URI mapování není součástí <xref:System.Xml.XPath.XPathNavigator> objektu kontextu novou deklaraci oboru názvů se přidá do nově vloženou uzlu.  
  
-   Pokud stejný identifikátor URI oboru názvů je v oboru jak <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale s jinou předponu k němu mapována v obou kontextech, přidá se do nově vloženou uzlu, s předponou novou deklaraci oboru názvů a identifikátor URI, které jsou převzaty z oboru názvů <xref:System.Xml.XmlReader> objektu.  
  
-   Pokud stejnou předponu oboru názvů je v oboru jak <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu nově vloženou uzel má jiný identifikátor URI oboru názvů k němu mapována v obou kontextech, se přidá novou deklaraci oboru názvů, ale které znovu deklaruje, že předpona s oborem názvů URI převzaty z <xref:System.Xml.XmlReader> objektu.  
  
-   Pokud předponu, jakož i identifikátor URI oboru názvů v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu je stejný, bez novou deklaraci oboru názvů se přidá do nově vloženou uzlu.  
  
> [!NOTE]
>  Výše uvedený popis platí také pro deklarace oboru názvů s prázdné `string` jako předpona (například výchozí deklaraci oboru názvů).  
  
 Toto jsou možné `xml:lang` je v konfliktu.  
  
-   Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XmlReader> kontextu objektu, ale ne v <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, `xml:lang` atribut, jehož hodnota je převzat ze <xref:System.Xml.XmlReader> objekt přidá do nově vloženou uzlu.  
  
-   Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, ale každý má jinou hodnotu, `xml:lang` atribut, jehož hodnota je převzat ze <xref:System.Xml.XmlReader> objekt přidá do nově vloženou uzlu.  
  
-   Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, ale každý se stejnou hodnotou, nové `xml:lang` atribut je přidaný na nově vloženou uzlu.  
  
-   Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, ale žádné existující v <xref:System.Xml.XmlReader> objektu kontextu, ne `xml:lang` přidání atributu do nově vloženou uzlu.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Vkládání uzly s XmlWriter  
 Jsou přetížené metody použité k vložení na stejné úrovni, podřízený a atribut uzlů, které jsou popsané v části "Vkládání uzlů a hodnoty". <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení uzlů.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nepodporované XmlWriter metody  
 Ne všechny metody použité k zápisu informací do dokumentu XML pomocí <xref:System.Xml.XmlWriter> třída podporuje <xref:System.Xml.XPath.XPathNavigator> třída kvůli rozdílu mezi XPath datového modelu a modelu objektu dokumentu (DOM).  
  
 V následující tabulce jsou popsány <xref:System.Xml.XmlWriter> metody, které nepodporují třídy <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Vyvolá <xref:System.NotSupportedException> výjimka.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignorovat na kořenové úrovni a generuje <xref:System.NotSupportedException> výjimka, pokud je volána na jiné úrovni v dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Považuje za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu ekvivalentní znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Považuje za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu ekvivalentní znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Považuje za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu ekvivalentní znak nebo znaky.|  
  
 Další informace o <xref:System.Xml.XmlWriter> naleznete <xref:System.Xml.XmlWriter> třídy referenční dokumentaci k nástroji.  
  
### <a name="multiple-xmlwriter-objects"></a>Více objektů XmlWriter  
 Je možné, že více <xref:System.Xml.XPath.XPathNavigator> objekty odkazující na různé části XML dokumentů s jeden nebo více otevřete <xref:System.Xml.XmlWriter> objekty. Více <xref:System.Xml.XmlWriter> jsou povoleny a podporován ve scénářích jednovláknové objekty.  
  
 Toto jsou důležité poznámky ke zvážení při použití více <xref:System.Xml.XmlWriter> objekty.  
  
-   Fragmenty kódu XML zapsaných správcem <xref:System.Xml.XmlWriter> objekty jsou přidány do souboru XML dokumentů, kdy <xref:System.Xml.XmlWriter.Close%2A> metoda jednotlivých <xref:System.Xml.XmlWriter> objektu se říká. Dokud nebude tento bod <xref:System.Xml.XmlWriter> objektu je zápis fragment odpojené. Pokud se provádí operace v dokumentu XML žádné fragmenty zapisovaný podle <xref:System.Xml.XmlWriter> objektu před <xref:System.Xml.XmlWriter.Close%2A> byla volána, neovlivní.  
  
-   Pokud dojde otevření <xref:System.Xml.XmlWriter> je odstraněn objekt na konkrétní podstrom XML a že podstrom, <xref:System.Xml.XmlWriter> objekt může přesto přidat do dílčí stromu. Podstrom jednoduše stane fragment odstraněné.  
  
-   Pokud je to více <xref:System.Xml.XmlWriter> objektů jsou otevřené na stejném místě v dokumentu XML, budou přidány do dokumentu XML v pořadí, ve kterém <xref:System.Xml.XmlWriter> objekty zavřou, není v pořadí, ve kterém byly otevřeny.  
  
 Následující příklad vytvoří <xref:System.Xml.XmlDocument> objektu, vytvoří <xref:System.Xml.XPath.XPathNavigator> objekt a používá <xref:System.Xml.XmlWriter> objekt vrácený <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodu pro vytvoření strukturu první seznam v `books.xml` souboru. Příklad pak uloží jej jako `book.xml` souboru.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a>Uložení dokumentu XML  
 Ukládají se změny provedené v <xref:System.Xml.XmlDocument> objektu jako výsledek metody popsané v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy. Další informace o ukládání změny <xref:System.Xml.XmlDocument> objektu, najdete v části [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování kódu XML dat pomocí jazyka XPath datový Model](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Upravit pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 [Odebrat pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
