---
title: Vložení dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b9eedfab68dc6aeacf9ed51ffc7205b73c062ca
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698336"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Vložení dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod pro vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML. Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, to znamená, jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML jsou vytvářeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití metod pro posunutí úprav <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený pomocí <xref:System.Xml.XPath.XPathDocument> výsledkem objektu <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Vkládání uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody pro vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML. Tyto metody umožňují vkládání uzlů a atributy v různých umístěních ve vztahu k aktuální pozici <xref:System.Xml.XPath.XPathNavigator> objektů a jsou popsané v následujících částech.  
  
### <a name="inserting-sibling-nodes"></a>Vkládání uzlů na stejné úrovni  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, chcete-li vložit uzlů na stejné úrovni.  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Tyto metody vložit na stejné úrovni uzly před a za uzel <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody jsou přetížené a přijmout `string`, <xref:System.Xml.XmlReader> objektu, nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje uzel na stejné úrovni jako parametry. Obě metody také vrátit <xref:System.Xml.XmlWriter> objekt používaný pro vkládání uzlů na stejné úrovni.  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody vložit jeden na stejné úrovni uzlu před a za uzel <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na použití předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.  
  
 V následujícím příkladu nový `pages` prvek se vloží před `price` první podřízený prvek `book` prvek `contosoBooks.xml` soubor.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody, naleznete v tématu <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci.  
  
### <a name="inserting-child-nodes"></a>Vkládání podřízené uzly  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, chcete-li vložit podřízené uzly.  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Tyto metody připojení a předřaďte podřízených uzlů na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.  
  
 Metody v části "Vkládání uzlů na stejné úrovni", jako jsou <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody přijímají `string`, <xref:System.Xml.XmlReader> objektu, nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje podřízený uzel, který chcete přidat jako parametry. Obě metody také vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení podřízené uzly.  
  
 Také, jako jsou metody v části "Vkládání uzlů na stejné úrovni" <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody vložit jeden podřízený uzel na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na použití Předpona oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.  
  
 V následujícím příkladu nový `pages` podřízený element je připojen k seznamu podřízených elementů prvního `book` prvek `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody, naleznete v tématu <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci.  
  
### <a name="inserting-attribute-nodes"></a>Vkládání uzlů atributů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, chcete-li vložit uzlů atributů.  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Tyto metody vložení, atribut uzlů na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda vytvoří uzel atributu na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na použití předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Vrátí metoda <xref:System.Xml.XmlWriter> objekt používaný pro vkládání uzlů atributů.  
  
 V následujícím příkladu, nové `discount` a `currency` atributy vytvořené na `price` podřízený element prvního `book` element v `contosoBooks.xml` soubor pomocí <xref:System.Xml.XmlWriter> objekt vrácený z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody, naleznete v tématu <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci.  
  
## <a name="copying-nodes"></a>Kopírování uzly  
 V některých případech můžete chtít naplnit dokument XML s obsahem z jiného dokumentu XML. Obě <xref:System.Xml.XPath.XPathNavigator> třídy a <xref:System.Xml.XmlWriter> třídy můžete kopírovat uzly <xref:System.Xml.XmlDocument> objekt z existující <xref:System.Xml.XmlReader> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy všechny mají přetížení, která může přijmout <xref:System.Xml.XPath.XPathNavigator> objektu nebo <xref:System.Xml.XmlReader> objektu jako parametr.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> Metodu <xref:System.Xml.XmlWriter> třída nemá přetížení, která může přijmout <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> objektu.  
  
 Následující příklad zkopíruje všechny `book` prvky z jednoho dokumentu do jiného.  
  
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
  
## <a name="inserting-values"></a>Vkládání hodnot  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody pro vložení hodnoty do uzlu <xref:System.Xml.XmlDocument> objektu.  
  
### <a name="inserting-untyped-values"></a>Vkládání Netypové hodnoty  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` předanou jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na. Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná pro typ uzlu, pokud je k dispozici informace o schématu.  
  
 V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Vkládání zadaných hodnot  
 Pokud je typ uzlu W3C XML schématu jednoduché zadejte, nová hodnota vkládat stisknutím <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda je porovnávána s omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavena. Pokud je nová hodnota není platná pro typ uzlu (například nastavíte hodnotu `-1` na element, jehož typ je `xs:positiveInteger`), je výsledkem výjimky.  
  
 V následujícím příkladu se pokusí změnit hodnotu `price` prvek první `book` prvek `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu. Protože typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` souborů, v důsledku výjimky.  
  
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
  
 V příkladu přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad využívá taky `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml a OuterXml vlastnosti  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na s analyzovaný obsah XML daného `string`. Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na i samotný uzel aktuální.  
  
 Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti slouží k vložení uzly a hodnoty v dokumentu XML. Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti, které chcete vložit uzly a hodnoty, najdete v článku [upravit dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespace a XML: lang – konflikty  
 Některé konflikty související se obor názvů a `xml:lang` deklarace může dojít při vkládání dat XML pomocí <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy, které využívají <xref:System.Xml.XmlReader>objektů jako parametry.  
  
 Tady jsou možné obor názvů konflikty.  
  
-   Pokud je obor názvů v obor v rámci <xref:System.Xml.XmlReader> objektu kontextu, kde není v předponu pro obor názvů identifikátoru URI mapování <xref:System.Xml.XPath.XPathNavigator> kontext objektu na nově vložený uzel se přidá nová deklarace oboru názvů.  
  
-   Pokud stejný obor názvů identifikátoru URI je v oboru v rámci i <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale má jinou předponu k němu mapována v obou kontextech, přidá novou deklaraci oboru názvů na nově vložený uzel s předponou a z identifikátoru URI oboru názvů <xref:System.Xml.XmlReader> objektu.  
  
-   Pokud stejnou předponu oboru názvů je v oboru v rámci i <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu nově vložený uzel má jiný obor názvů identifikátoru URI k němu mapována v obou kontextech, se přidá nová deklarace oboru názvů, ale které znovu deklaruje tuto předponu oboru názvů identifikátoru URI na základě <xref:System.Xml.XmlReader> objektu.  
  
-   Pokud předponu, stejně jako obor názvů URI v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu je stejný, bez nové deklarace oboru názvů se přidá na nově vložený uzel.  
  
> [!NOTE]
>  Výše uvedený popis platí také pro deklarace oboru názvů s prázdnou `string` jako předpona (například výchozí deklaraci oboru názvů).  
  
 Toto jsou možné `xml:lang` je v konfliktu.  
  
-   Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XmlReader> objektu kontextu, ale ne v <xref:System.Xml.XPath.XPathNavigator> kontext objektu `xml:lang` atribut, jehož hodnota je převzata z <xref:System.Xml.XmlReader> je objekt přidán na nově vložený uzel.  
  
-   Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale každý má jinou hodnotu, `xml:lang` atribut, jehož hodnota je převzata z <xref:System.Xml.XmlReader> objekt je přidat do nově vložený uzel.  
  
-   Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale každý se stejnou hodnotou, nové `xml:lang` přidat atribut na nově vložený uzel.  
  
-   Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale žádné existující v <xref:System.Xml.XmlReader> objektu kontextu, ne `xml:lang` přidat atribut na nově vložený uzel.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Vkládání uzlů s XmlWriter  
 Jsou přetížené metody použité k vložení na stejné úrovni, podřízený a atribut uzly, které jsou popsané v části "Vkládání uzlů a hodnoty". <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení uzlů.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nepodporovaný objekt XmlWriter metody  
 Některé z metod používaných pro zápis do dokumentu XML pomocí informací <xref:System.Xml.XmlWriter> třídy jsou podporovány <xref:System.Xml.XPath.XPathNavigator> třídy kvůli rozdílu mezi modelu dat XPath a Document Object Model (DOM).  
  
 V následující tabulce jsou popsány <xref:System.Xml.XmlWriter> metody, které nepodporují třídy <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Vyvolá výjimku <xref:System.NotSupportedException> výjimky.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Na kořenové úrovni a vyvolá výjimku Ignorovat <xref:System.NotSupportedException> výjimky-li volána na jiné úrovni v dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Považováno za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu pro odpovídající znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Považováno za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu pro odpovídající znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Považováno za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu pro odpovídající znak nebo znaky.|  
  
 Další informace o <xref:System.Xml.XmlWriter> najdete v tématu <xref:System.Xml.XmlWriter> třídy referenční dokumentaci.  
  
### <a name="multiple-xmlwriter-objects"></a>Více objektů XmlWriter  
 Je možné mít více <xref:System.Xml.XPath.XPathNavigator> objekty odkazující na různé části XML dokument otevřít jeden nebo více <xref:System.Xml.XmlWriter> objekty. Více <xref:System.Xml.XmlWriter> objekty jsou povolené a podporován ve scénářích s jedním vláknem.  
  
 Tady jsou důležité poznámky ke zvážení při použití více <xref:System.Xml.XmlWriter> objekty.  
  
-   Fragmenty XML autorem <xref:System.Xml.XmlWriter> objekty jsou přidány do souboru XML dokumentů, kdy <xref:System.Xml.XmlWriter.Close%2A> metoda jednotlivých <xref:System.Xml.XmlWriter> objekt, se nazývá. Do tohoto bodu <xref:System.Xml.XmlWriter> objekt zapisuje odpojené fragment. Pokud se operace provádí v dokumentu XML, jakékoli fragmenty jsou zapsána pomocí <xref:System.Xml.XmlWriter> objektu před <xref:System.Xml.XmlWriter.Close%2A> byla volána, nejsou ovlivněny.  
  
-   Pokud není otevřený <xref:System.Xml.XmlWriter> odstranění objektu na konkrétní podstrom XML a že podstrom <xref:System.Xml.XmlWriter> objekt může přesto přidat do dílčí stromu. Podstrom jednoduše stane odstraněné fragment.  
  
-   Pokud je položek víc <xref:System.Xml.XmlWriter> objektů jsou otevřené na stejné místo v dokumentu XML, jsou přidány do dokumentu XML v pořadí, ve kterém <xref:System.Xml.XmlWriter> objektů jsou uzavřeny, ne v pořadí, v jakém byly otevřeny.  
  
 Následující příklad vytvoří <xref:System.Xml.XmlDocument> objektu, vytvoří <xref:System.Xml.XPath.XPathNavigator> a pak použije <xref:System.Xml.XmlWriter> objekt vrácený <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodu pro vytvoření struktury první adresáře v `books.xml` souboru. Jako příklad pak uloží `book.xml` souboru.  
  
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
 Ukládají se změny provedené <xref:System.Xml.XmlDocument> objekt výsledku z metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy. Další informace o uložení změny <xref:System.Xml.XmlDocument> objektu, najdete v článku [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Změna dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
- [Odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
