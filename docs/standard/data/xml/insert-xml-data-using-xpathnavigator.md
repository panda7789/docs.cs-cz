---
title: Vložení dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 68c003467d837fe79d5e275968e47fa5dc3490cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710723"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>Vložení dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML. Aby bylo možné tyto metody použít, musí <xref:System.Xml.XPath.XPathNavigator> být objekt upravitelný, to znamená, že <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> jeho vlastnost musí `true`být.  
  
 <xref:System.Xml.XPath.XPathNavigator>objekty, které mohou upravovat dokument XML, jsou vytvořeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodou <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav <xref:System.Xml.XPath.XPathNavigator> objektu vytvořeného <xref:System.Xml.XPath.XPathDocument> objektem mají za následek. <xref:System.NotSupportedException>  
  
 Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Vkládání uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody pro vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML. Tyto metody umožňují vkládat uzly a atributy v různých umístěních ve vztahu k aktuální pozici <xref:System.Xml.XPath.XPathNavigator> objektu a jsou popsány v následujících částech.  
  
### <a name="inserting-sibling-nodes"></a>Vkládání uzlů na stejné úrovni  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody pro vložení uzlů na stejné úrovni.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Tyto metody vloží uzly stejné úrovně před a za uzlem <xref:System.Xml.XPath.XPathNavigator> , na kterém je objekt aktuálně umístěný.  
  
 Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> jsou přetížené a přijímají `string` <xref:System.Xml.XmlReader> objekt, objekt nebo <xref:System.Xml.XPath.XPathNavigator> objekt obsahující uzel na stejné úrovni, který se přidá jako parametry. Obě metody také vracejí <xref:System.Xml.XmlWriter> objekt, který slouží k vložení uzlů na stejné úrovni.  
  
 Metody <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> vkládají jeden uzel na stejné úrovni před a po uzlu, na <xref:System.Xml.XPath.XPathNavigator> kterém je objekt aktuálně umístěný, pomocí předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.  
  
 `pages` V následujícím příkladu je nový prvek vložen před `price` podřízený prvek prvního `book` prvku v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> naleznete v referenční dokumentaci <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
### <a name="inserting-child-nodes"></a>Vkládání podřízených uzlů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody pro vložení podřízených uzlů.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Tyto metody připojí a odřadí podřízené uzly na konec a začátek seznamu podřízených uzlů uzlu, na kterém je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn.  
  
 Podobně jako metody v části "vložení uzlů stejné úrovně", metody <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> přijímají `string`, <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje podřízený uzel, který chcete přidat jako parametry. Obě metody také vracejí <xref:System.Xml.XmlWriter> objekt, který slouží k vložení podřízených uzlů.  
  
 Stejně jako metody v části "vložení uzlů stejné úrovně", metody <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> vkládají jeden podřízený uzel na konec a začátek seznamu podřízených uzlů uzlu, na kterém je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný, pomocí předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.  
  
 V následujícím příkladu je nový `pages` podřízený element připojen do seznamu podřízených prvků prvního `book` prvku v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> naleznete v referenční dokumentaci <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
### <a name="inserting-attribute-nodes"></a>Vkládání uzlů atributů  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody pro vložení uzlů atributů.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Tyto metody vkládají uzly atributů v uzlu element, na <xref:System.Xml.XPath.XPathNavigator> kterém je objekt aktuálně umístěný. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda vytvoří uzel atributu v uzlu element a <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na základě předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda vrátí <xref:System.Xml.XmlWriter> objekt použitý pro vložení uzlů atributu.  
  
 V následujícím příkladu jsou vytvořeny nové `discount` a `currency` atributy `price` v podřízeném prvku `book` prvního prvku v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XmlWriter> objektu vráceného z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> naleznete v <xref:System.Xml.XPath.XPathNavigator> referenční dokumentaci třídy.  
  
## <a name="copying-nodes"></a>Kopírování uzlů  
 V některých případech může být vhodné naplnit dokument XML obsahem z jiného dokumentu XML. <xref:System.Xml.XPath.XPathNavigator> Třída i <xref:System.Xml.XmlWriter> třída mohou kopírovat uzly do <xref:System.Xml.XmlDocument> objektu z existujícího <xref:System.Xml.XmlReader> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu.  
  
 Metody <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator> třídy All mají přetížení, které mohou přijmout <xref:System.Xml.XPath.XPathNavigator> objekt nebo <xref:System.Xml.XmlReader> objekt jako parametr.  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> Metoda <xref:System.Xml.XmlWriter> třídy má přetížení, které může přijmout objekt <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>nebo. <xref:System.Xml.XPath.XPathNavigator>  
  
 Následující příklad zkopíruje všechny `book` prvky z jednoho dokumentu do druhého.  
  
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
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> pro vkládání hodnot pro uzel do <xref:System.Xml.XmlDocument> objektu.  
  
### <a name="inserting-untyped-values"></a>Vkládání netypových hodnot  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnoty předané jako parametr jako hodnotu uzlu, na kterém <xref:System.Xml.XPath.XPathNavigator> je objekt aktuálně umístěn. Hodnota je vložena bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud jsou k dispozici informace o schématu.  
  
 V následujícím příkladu je <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda použita k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Vkládání zadaných hodnot  
 Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodou zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` na elementu, jehož typ je `xs:positiveInteger`), výsledkem je výjimka.  
  
 Následující příklad `price` se pokusí změnit hodnotu prvku prvního `book` prvku v `contosoBooks.xml` souboru na <xref:System.DateTime> hodnotu. Vzhledem k tomu, že typ schématu `price` XML elementu je definován `xs:decimal` jako v `contosoBooks.xsd` souborech, výsledkem je výjimka.  
  
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
  
 Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Vlastnosti InnerXml a OuterXml  
 Vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator> třídy <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> a třídy mění kód XML uzlů, na kterých je objekt aktuálně umístěn.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost změní kód XML podřízených uzlů, na kterých je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn, s analyzovaným obsahem daného XML `string`. Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost mění kód XML podřízených uzlů, na kterých je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn, i v samotném aktuálním uzlu.  
  
 Kromě metod popsaných v tomto tématu lze vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> použít k vložení uzlů a hodnot v dokumentu XML. Další informace o použití vlastností <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> k vložení uzlů a hodnot naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespaces and XML: lang – konflikty  
 Některé konflikty související s rozsahem oboru názvů a `xml:lang` deklarace mohou nastat při vkládání dat XML pomocí metod <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator> třídy, které přebírají <xref:System.Xml.XmlReader> objekty jako parametry.  
  
 Níže jsou uvedené možné konflikty oboru názvů.  
  
- Pokud v kontextu <xref:System.Xml.XmlReader> objektu existuje obor názvů v oboru, kde předpona na mapování identifikátoru URI oboru názvů není v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, je přidána nová deklarace oboru názvů do nově vloženého uzlu.  
  
- Pokud je stejný identifikátor URI oboru názvů v rámci kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale má v obou kontextech mapována jiná předpona, nová deklarace oboru názvů je přidána do nově vloženého uzlu s předponou a identifikátorem URI oboru názvů provedeným z <xref:System.Xml.XmlReader> objektu.  
  
- Pokud je stejná předpona oboru názvů v rámci kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale má v obou KONTEXTECH mapován jiný identifikátor URI oboru názvů, nová deklarace oboru názvů je přidána do nově vloženého uzlu, který znovu deklaruje tuto předponu s identifikátorem URI oboru názvů provedeným z <xref:System.Xml.XmlReader> objektu.  
  
- Pokud je předpona a také identifikátor URI oboru názvů v kontextu <xref:System.Xml.XmlReader> objektu i kontext <xref:System.Xml.XPath.XPathNavigator> objektu stejný, není do nově vloženého uzlu přidána žádná nová deklarace oboru názvů.  
  
> [!NOTE]
> Výše uvedený popis platí také pro deklarace oboru názvů s prázdným `string` argumentem jako předponu (například výchozí deklarace oboru názvů).  
  
 Níže jsou uvedené možné `xml:lang` konflikty.  
  
- Pokud `xml:lang` existuje atribut v oboru v kontextu <xref:System.Xml.XmlReader> objektu, ale ne v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, je `xml:lang` atribut, jehož hodnota je převedena z <xref:System.Xml.XmlReader> objektu, přidán do nově vloženého uzlu.  
  
- Pokud `xml:lang` existuje atribut v oboru v kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale každý má jinou hodnotu, `xml:lang` atribut, jehož hodnota je převedena z <xref:System.Xml.XmlReader> objektu, je přidán do nově vloženého uzlu.  
  
- Pokud existuje `xml:lang` atribut v oboru v kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale každý se stejnou hodnotou, není do nově vloženého uzlu přidán žádný nový `xml:lang` atribut.  
  
- Pokud existuje `xml:lang` atribut v oboru v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale žádný existující v kontextu <xref:System.Xml.XmlReader> objektu, není do nově vloženého uzlu přidán žádný `xml:lang` atribut.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Vkládání uzlů pomocí XmlWriter  
 Metody použité pro vložení uzlů na stejné úrovni, podřízené a atributy popsané v části vkládání uzlů a hodnot jsou přetíženy. Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> a <xref:System.Xml.XPath.XPathNavigator> třídy vracejí <xref:System.Xml.XmlWriter> objekt, který se používá pro vkládání uzlů.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nepodporované metody XmlWriter  
 Ne všechny metody použité pro zápis informací do dokumentu XML pomocí <xref:System.Xml.XmlWriter> třídy jsou podporovány <xref:System.Xml.XPath.XPathNavigator> třídou z důvodu rozdílu mezi datovým modelem XPath a model DOM (Document Object Model) (DOM).  
  
 Následující tabulka popisuje metody <xref:System.Xml.XmlWriter> třídy, které <xref:System.Xml.XPath.XPathNavigator> Třída nepodporuje.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Vyvolá <xref:System.NotSupportedException> výjimku.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignoruje se na kořenové úrovni a vyvolá <xref:System.NotSupportedException> výjimku, pokud je volána na jakékoli jiné úrovni dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Považuje se za volání <xref:System.Xml.XmlWriter.WriteString%2A> metody pro ekvivalentní znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Považuje se za volání <xref:System.Xml.XmlWriter.WriteString%2A> metody pro ekvivalentní znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Považuje se za volání <xref:System.Xml.XmlWriter.WriteString%2A> metody pro ekvivalentní znak nebo znaky.|  
  
 Další informace o <xref:System.Xml.XmlWriter> třídě naleznete v <xref:System.Xml.XmlWriter> referenční dokumentaci třídy.  
  
### <a name="multiple-xmlwriter-objects"></a>Více objektů XmlWriter  
 Je možné mít více <xref:System.Xml.XPath.XPathNavigator> objektů odkazujících na různé části dokumentu XML s jedním nebo více otevřenými <xref:System.Xml.XmlWriter> objekty. Ve <xref:System.Xml.XmlWriter> scénářích s jedním vláknem je povoleno a podporováno více objektů.  
  
 V následujícím seznamu jsou důležité poznámky, které je potřeba <xref:System.Xml.XmlWriter> vzít v úvahu při použití více objektů.  
  
- Fragmenty XML napsané <xref:System.Xml.XmlWriter> objekty jsou přidány do dokumentu XML, pokud <xref:System.Xml.XmlWriter.Close%2A> je volána metoda <xref:System.Xml.XmlWriter> každého objektu. Do tohoto okamžiku <xref:System.Xml.XmlWriter> objekt zapisuje odpojený fragment. Pokud je operace provedena v dokumentu XML, nebudou ovlivněny všechny fragmenty, které <xref:System.Xml.XmlWriter> jsou zapsány <xref:System.Xml.XmlWriter.Close%2A> objektem před voláním.  
  
- Pokud je otevřený <xref:System.Xml.XmlWriter> objekt v konkrétním podstromu XML a tento podstrom je odstraněn, <xref:System.Xml.XmlWriter> objekt může být stále přidán do podstromu. Podstrom se jednoduše odstraněný fragmentem.  
  
- Pokud je <xref:System.Xml.XmlWriter> otevřeno více objektů ve stejném okamžiku v dokumentu XML, jsou přidány do dokumentu XML v pořadí, ve kterém byly <xref:System.Xml.XmlWriter> objekty uzavřeny, nikoli v pořadí, v jakém byly otevřeny.  
  
 Následující příklad vytvoří <xref:System.Xml.XmlDocument> objekt, vytvoří <xref:System.Xml.XPath.XPathNavigator> objekt a poté pomocí <xref:System.Xml.XmlWriter> objektu vráceného <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodou vytvoří strukturu první knihy v `books.xml` souboru. Příklad ho uloží jako `book.xml` soubor.  
  
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
 Uložení změn provedených v <xref:System.Xml.XmlDocument> objektu jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy. Další informace o ukládání změn provedených v <xref:System.Xml.XmlDocument> objektu naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Změna dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [Odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
