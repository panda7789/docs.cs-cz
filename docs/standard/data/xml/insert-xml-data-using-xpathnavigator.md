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
Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML. Aby bylo možné použít tyto metody, objekt <xref:System.Xml.XPath.XPathNavigator> musí být upravitelný, to znamená, že jeho vlastnost <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> objektů, které mohou upravovat dokument XML, jsou vytvořeny metodou <xref:System.Xml.XmlDocument.CreateNavigator%2A> třídy <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav objektu <xref:System.Xml.XPath.XPathNavigator> vytvořeného objektem <xref:System.Xml.XPath.XPathDocument> mají za následek <xref:System.NotSupportedException>.  
  
 Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů naleznete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="inserting-nodes"></a>Vkládání uzlů  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje metody pro vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML. Tyto metody umožňují vkládat uzly a atributy v různých umístěních ve vztahu k aktuální pozici objektu <xref:System.Xml.XPath.XPathNavigator> a jsou popsány v následujících částech.  
  
### <a name="inserting-sibling-nodes"></a>Vkládání uzlů na stejné úrovni  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje následující metody pro vložení uzlů na stejné úrovni.  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 Tyto metody vloží uzly stejné úrovně před a po uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný.  
  
 Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> jsou přetížené a přijímají objekt `string`, <xref:System.Xml.XmlReader> nebo objekt <xref:System.Xml.XPath.XPathNavigator> obsahující uzel na stejné úrovni, který se přidá jako parametry. Obě metody také vracejí objekt <xref:System.Xml.XmlWriter>, který slouží k vložení uzlů na stejné úrovni.  
  
 Metody <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> vloží jeden uzel na stejné úrovni před a po uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný, pomocí předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.  
  
 V následujícím příkladu je vložen nový prvek `pages` před `price` podřízený prvek prvního `book` elementu v souboru `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metod naleznete v dokumentaci třídy <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="inserting-child-nodes"></a>Vkládání podřízených uzlů  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje následující metody pro vložení podřízených uzlů.  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 Tyto metody připojí a odřadí podřízené uzly na konec a začátek seznamu podřízených uzlů uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný.  
  
 Podobně jako metody v části "vložení uzlů na stejné úrovni" metody <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> přijímají `string`, objekt <xref:System.Xml.XmlReader> nebo objekt <xref:System.Xml.XPath.XPathNavigator> obsahující podřízený uzel, který chcete přidat jako parametry. Obě metody také vracejí objekt <xref:System.Xml.XmlWriter>, který se používá pro vložení podřízených uzlů.  
  
 Podobně jako metody v části "vložení uzlů na stejné úrovni" metody <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> vloží jeden podřízený uzel na konec a začátek seznamu podřízených uzlů uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný, na základě předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.  
  
 V následujícím příkladu je nový `pages` podřízený element připojen k seznamu podřízených prvků prvního prvku `book` v souboru `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metod naleznete v dokumentaci třídy <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="inserting-attribute-nodes"></a>Vkládání uzlů atributů  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje následující metody pro vkládání uzlů atributů.  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 Tyto metody vkládají uzly atributů na uzel elementu, kde je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný. Metoda <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> vytvoří uzel atributu v uzlu element. objekt <xref:System.Xml.XPath.XPathNavigator> je aktuálně umístěn na základě předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry. Metoda <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> vrátí objekt <xref:System.Xml.XmlWriter>, který se používá pro vložení uzlů atributu.  
  
 V následujícím příkladu jsou vytvořeny nové `discount` a `currency` atributy v `price` podřízený prvek prvního `book` prvku v souboru `contosoBooks.xml` pomocí objektu <xref:System.Xml.XmlWriter> vráceného z metody <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>.  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> naleznete v dokumentaci třídy <xref:System.Xml.XPath.XPathNavigator> reference.  
  
## <a name="copying-nodes"></a>Kopírování uzlů  
 V některých případech může být vhodné naplnit dokument XML obsahem z jiného dokumentu XML. Třída <xref:System.Xml.XPath.XPathNavigator> i třída <xref:System.Xml.XmlWriter> mohou kopírovat uzly do objektu <xref:System.Xml.XmlDocument> z existujícího objektu <xref:System.Xml.XmlReader> nebo objektu <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody třídy <xref:System.Xml.XPath.XPathNavigator> mají přetížení, které mohou přijmout objekt <xref:System.Xml.XPath.XPathNavigator> nebo objekt <xref:System.Xml.XmlReader> jako parametr.  
  
 Metoda <xref:System.Xml.XmlWriter.WriteNode%2A> třídy <xref:System.Xml.XmlWriter> má přetížení, které může přijmout objekt <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>nebo <xref:System.Xml.XPath.XPathNavigator>.  
  
 Následující příklad zkopíruje všechny prvky `book` z jednoho dokumentu do druhého.  
  
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
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> pro vkládání hodnot pro uzel do objektu <xref:System.Xml.XmlDocument>.  
  
### <a name="inserting-untyped-values"></a>Vkládání netypových hodnot  
 Metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> jednoduše vloží Netypový `string` hodnotu předanou jako parametr jako hodnotu uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný. Hodnota je vložena bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud jsou k dispozici informace o schématu.  
  
 V následujícím příkladu je použita metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> k aktualizaci všech prvků `price` v souboru `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>Vkládání zadaných hodnot  
 Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená metodou <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty. Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem bude výjimka.  
  
 Následující příklad se pokusí změnit hodnotu prvku `price` prvního prvku `book` v souboru `contosoBooks.xml` na <xref:System.DateTime>ou hodnotu. Vzhledem k tomu, že typ schématu XML prvku `price` je definován jako `xs:decimal` v souborech `contosoBooks.xsd`, výsledkem je výjimka.  
  
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
  
 Příklad přebírá soubor `contosoBooks.xml` jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Příklad také přebírá `contosoBooks.xsd` jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a>Vlastnosti InnerXml a OuterXml  
 Vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> třídy <xref:System.Xml.XPath.XPathNavigator> mění kód XML uzlů, na kterých je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěn.  
  
 Vlastnost <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> změní kód XML podřízených uzlů, na kterých je aktuálně umístěn <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje analyzovaný obsah daného XML `string`. Podobně vlastnost <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mění kód XML podřízených uzlů, na kterých je aktuálně umístěn <xref:System.Xml.XPath.XPathNavigator> objekt a také na samotném aktuálním uzlu.  
  
 Kromě metod popsaných v tomto tématu, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastností lze použít k vložení uzlů a hodnot do dokumentu XML. Další informace o použití <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastností pro vkládání uzlů a hodnot naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
## <a name="namespace-and-xmllang-conflicts"></a>Namespaces and XML: lang – konflikty  
 Při vkládání dat XML pomocí <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>ch metod třídy <xref:System.Xml.XPath.XPathNavigator>, které jako parametry přebírají <xref:System.Xml.XmlReader> objekty, může dojít k určitým konfliktům souvisejícím s oborem oboru názvů a `xml:lang` deklarací.  
  
 Níže jsou uvedené možné konflikty oboru názvů.  
  
- Pokud je obor názvů v oboru v kontextu <xref:System.Xml.XmlReader>ho objektu, kde předpona na mapování identifikátoru URI oboru názvů není v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, je do nově vloženého uzlu přidána deklarace nového oboru názvů.  
  
- Pokud je stejný identifikátor URI oboru názvů v rámci kontextu objektu <xref:System.Xml.XmlReader> a kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale v obou kontextech je namapovaný jiný prefix, nová deklarace oboru názvů je přidána do nově vloženého uzlu s předponou a identifikátorem URI oboru názvů provedenými z objektu <xref:System.Xml.XmlReader>.  
  
- Je-li stejná předpona oboru názvů v rámci kontextu objektu <xref:System.Xml.XmlReader> a kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale má v obou kontextech namapován jiný identifikátor URI oboru názvů, nová deklarace oboru názvů je přidána do nově vloženého uzlu, který znovu deklaruje tuto předponu s identifikátorem URI oboru názvů provedeným z objektu <xref:System.Xml.XmlReader>.  
  
- Pokud je předpona i identifikátor URI oboru názvů jak v kontextu objektu <xref:System.Xml.XmlReader>, tak v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, do nově vloženého uzlu není přidána žádná nová deklarace oboru názvů.  
  
> [!NOTE]
> Výše uvedený popis platí také pro deklarace oboru názvů s prázdným `string` jako předponu (například výchozí deklarace oboru názvů).  
  
 Níže jsou uvedené možné konflikty `xml:lang`.  
  
- Pokud je atribut `xml:lang` v oboru v rámci kontextu <xref:System.Xml.XmlReader> objektu, ale ne v kontextu objektu <xref:System.Xml.XPath.XPathNavigator>, atribut `xml:lang`, jehož hodnota je předávána z objektu <xref:System.Xml.XmlReader>, je přidán do nově vloženého uzlu.  
  
- Pokud existuje atribut `xml:lang` v oboru v kontextu <xref:System.Xml.XmlReader> objektu a kontextu objektu <xref:System.Xml.XPath.XPathNavigator>, ale každá má jinou hodnotu, atribut `xml:lang`, jehož hodnota je předávána z objektu <xref:System.Xml.XmlReader>, je přidána do nově vloženého uzlu.  
  
- Pokud existuje atribut `xml:lang` v oboru v kontextu <xref:System.Xml.XmlReader> objektu a kontextu objektu <xref:System.Xml.XPath.XPathNavigator>, ale každý se stejnou hodnotou, není do nově vloženého uzlu přidán žádný nový atribut `xml:lang`.  
  
- Pokud v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu existuje atribut `xml:lang` v oboru, ale žádná existující v kontextu objektu <xref:System.Xml.XmlReader>, není do nově vloženého uzlu přidána žádná `xml:lang` atributu.  
  
## <a name="inserting-nodes-with-xmlwriter"></a>Vkládání uzlů pomocí XmlWriter  
 Metody použité pro vložení uzlů na stejné úrovni, podřízené a atributy popsané v části vkládání uzlů a hodnot jsou přetíženy. Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> třídy <xref:System.Xml.XPath.XPathNavigator> vrátí objekt <xref:System.Xml.XmlWriter>, který se používá pro vkládání uzlů.  
  
### <a name="unsupported-xmlwriter-methods"></a>Nepodporované metody XmlWriter  
 Ne všechny metody, které jsou použity pro zápis informací do dokumentu XML pomocí třídy <xref:System.Xml.XmlWriter>, jsou podporovány třídou <xref:System.Xml.XPath.XPathNavigator> z důvodu rozdílu mezi datovým modelem XPath a model DOM (Document Object Model) (DOM).  
  
 Následující tabulka popisuje metody třídy <xref:System.Xml.XmlWriter>, které nejsou podporovány třídou <xref:System.Xml.XPath.XPathNavigator>.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|Vyvolá výjimku <xref:System.NotSupportedException>.|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|Ignoruje se na kořenové úrovni a vyvolá výjimku <xref:System.NotSupportedException>, pokud je volána na jakékoli jiné úrovni dokumentu XML.|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|Je považována za volání metody <xref:System.Xml.XmlWriter.WriteString%2A> pro ekvivalentní znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|Je považována za volání metody <xref:System.Xml.XmlWriter.WriteString%2A> pro ekvivalentní znak nebo znaky.|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|Je považována za volání metody <xref:System.Xml.XmlWriter.WriteString%2A> pro ekvivalentní znak nebo znaky.|  
  
 Další informace o třídě <xref:System.Xml.XmlWriter> naleznete v referenční dokumentaci třídy <xref:System.Xml.XmlWriter>.  
  
### <a name="multiple-xmlwriter-objects"></a>Více objektů XmlWriter  
 Je možné mít více <xref:System.Xml.XPath.XPathNavigator> objektů odkazujících na různé části dokumentu XML s jedním nebo více otevřenými objekty <xref:System.Xml.XmlWriter>. Ve scénářích s jedním vláknem je povoleno a podporováno více objektů <xref:System.Xml.XmlWriter>.  
  
 V následujícím seznamu jsou důležité poznámky, které je potřeba vzít v úvahu při používání více <xref:System.Xml.XmlWriter> objektů.  
  
- Fragmenty XML napsané <xref:System.Xml.XmlWriter> objekty jsou přidány do dokumentu XML při volání metody <xref:System.Xml.XmlWriter.Close%2A> každého objektu <xref:System.Xml.XmlWriter>. Až do tohoto okamžiku, objekt <xref:System.Xml.XmlWriter> zapisuje odpojený fragment. Pokud je operace provedena v dokumentu XML, nebudou ovlivněny všechny fragmenty, které jsou zapsány objektem <xref:System.Xml.XmlWriter> před voláním <xref:System.Xml.XmlWriter.Close%2A>.  
  
- Pokud je otevřený objekt <xref:System.Xml.XmlWriter> v konkrétním podstromu XML a tento podstrom je odstraněn, může být objekt <xref:System.Xml.XmlWriter> stále přidán do podstromu. Podstrom se jednoduše odstraněný fragmentem.  
  
- Pokud je v dokumentu XML otevřeno více objektů <xref:System.Xml.XmlWriter>, jsou přidány do dokumentu XML v pořadí, ve kterém byly objekty <xref:System.Xml.XmlWriter> uzavřeny, nikoli v pořadí, ve kterém byly otevřeny.  
  
 Následující příklad vytvoří objekt <xref:System.Xml.XmlDocument>, vytvoří objekt <xref:System.Xml.XPath.XPathNavigator> a poté pomocí objektu <xref:System.Xml.XmlWriter> vráceného metodou <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> vytvoří strukturu první knihy v souboru `books.xml`. Příklad ho uloží jako soubor `book.xml`.  
  
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
 Uložení změn provedených v objektu <xref:System.Xml.XmlDocument> jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy. Další informace o uložení změn provedených v objektu <xref:System.Xml.XmlDocument> naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Změna dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [Odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
