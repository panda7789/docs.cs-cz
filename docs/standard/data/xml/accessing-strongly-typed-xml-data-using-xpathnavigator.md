---
title: Přístup k silně typované dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c283d3c87effcf9e898bb769cc8991da6cea453
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199619"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Přístup k silně typované dat XML pomocí XPathNavigator
Jako instanci datového modelu, XPath 2.0 <xref:System.Xml.XPath.XPathNavigator> třídy mohou obsahovat silného typu dat, která se mapuje na common language runtime (CLR) typy. Podle modelu dat XPath 2.0 může obsahovat pouze prvky a atributy dat silného typu. <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje mechanismus pro přístup k datům v rámci <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> jako silného typu dat, stejně jako mechanismus pro převod z jednoho datového typu na jiný objekt.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informace o typu vystavené objektem XPathNavigator nastaveným na  
 Data XML 1.0 je technicky bez typu, pokud zpracovává se DTD, XML definice jazyk (XSD) schématu nebo jinému kontrolnímu mechanismu. Existuje mnoho kategorií informací o typu, který může být přidružen k elementu XML nebo atributu.  
  
-   Jednoduché typy CLR: Žádný z těchto jazyků schématu XML nepodporuje typy Common Language Runtime (CLR) přímo. Protože je výhodné mít možnost zobrazit jednoduchý prvek a obsah atributů jako nejvhodnější typ CLR, všechny jednoduchý obsah lze zadat jako <xref:System.String> chybí informace o schématu s žádným přidány informace o schématu potenciálně upřesnění tento obsah více příslušného typu. Můžete najít nejvhodnější typ CLR jednoduchý obsah elementu a atribut s použitím <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> vlastnost. Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Seznam typů jednoduchých (CLR): elementu nebo atributu s jednoduchým obsahem může obsahovat seznam hodnoty oddělené symbolem mezery. Hodnoty jsou určena pomocí schématu XML jako "typ seznamu". Chybí schématu XML budou považované za jeden textový uzel takové jednoduchý obsah. Pokud schéma XML je k dispozici, může být tento jednoduchý obsah vystavena jako hodnoty řadu atomických, každý s jednoduchý typ, který se mapuje na kolekci objektů CLR. Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Zadaná hodnota: Ověření schématu atribut nebo element s jednoduchý typ má zadanou hodnotou. Tato hodnota je primitivní typ, jako je například číselná, řetězec nebo typ date. Všechny integrované jednoduché typy v XSD je možné mapovat na typy CLR, které poskytují přístup k hodnotě uzel jako vhodnější typ namísto pouze jako <xref:System.String>. Element s atributy nebo podřízené položky elementu se považuje za komplexní. Zadaná hodnota komplexní typ s jednoduchým obsahem (pouze textové uzly jako podřízené objekty) je stejné jako u jednoduchého typu jeho obsahu. Zadaná hodnota komplexní typ se složitým obsahem (jeden nebo více podřízených prvků) je zřetězení všechny jeho podřízené uzly text vrácena jako hodnotu řetězce <xref:System.String>. Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Jazyk schématu konkrétní název typu: Ve většině případů typů CLR, které jsou nastavené jako vedlejší efekt použití externí schéma, slouží k poskytnutí přístupu k hodnotě uzlu. Mohou však nastat situace, kde můžete prozkoumat typ přidružený k konkrétní schématu použitého pro dokument XML. Například můžete chtít Hledat v dokumentu XML, extrahování všechny elementy, které jsou určeny s obsahem typu "PurchaseOrder" podle připojených schématu. Tyto informace o typu lze nastavit pouze v důsledku ověřování schématu a tyto informace se přistupuje přes <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> a <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy. Další informace naleznete v části příspěvku schématu ověření informační sada (PSVI) níže.  
  
-   Reflexe konkrétní jazyk schématu: V jiných případech můžete chtít získat další podrobnosti o konkrétní schématu typu použitý pro dokument XML. Například při čtení souboru XML, můžete k extrakci `maxOccurs` atribut pro každý platný uzel v dokumentu XML, aby bylo možné provést některé vlastní výpočet. Protože tyto informace je nastavena pouze pomocí ověření schématu, je přístupný prostřednictvím <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy. Další informace naleznete v části příspěvku schématu ověření informační sada (PSVI) níže.  
  
## <a name="xpathnavigator-typed-accessors"></a>XPathNavigator zadali přístupové objekty  
 V následující tabulce jsou uvedeny různé vlastnosti a metody <xref:System.Xml.XPath.XPathNavigator> třídu, která umožňuje přístup k informacím o typu o uzlu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Pokud je platný obsahuje informace o typu schématu XML pro uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Tato položka obsahuje schéma po ověření informační sadu uzlu, které se přidají po ověření. To zahrnuje informace o typu schématu XML, jakož i informace platnosti.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Typ CLR hodnotu typu uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Obsah uzlu CLR jeden nebo více hodnot, jehož typ je nejvíce odpovídá schématu XML typu uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Boolean> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.DateTime> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Double> hodnoty, podle pravidla přetypování XPath 2.0 pro `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Int32> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Int64> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Obsah uzlu přetypovat na typ cíle podle pravidel přetypování XPath 2.0.|  
  
 Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Příspěvek schéma ověřování v informační sadu (PSVI)  
 Procesor schématu XML přijímá informační sadu XML jako vstup a převede jej do schéma ověření informační sada (PSVI Post). PSVI je původní vstupní XML informační sadu se nové informace položky přidané a přidání existující položky informace nových vlastností. Existují tři různé třídy informací pro informační sadu XML v PSVI, které jsou vystavené <xref:System.Xml.XPath.XPathNavigator>.  
  
1.  Výsledky ověření: Informace o tom, zda elementu nebo atributu byl úspěšně ověřen nebo ne. To je zveřejněný prostřednictvím <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
2.  Výchozí informace: Označení, zda hodnota elementu nebo atributu byl získán prostřednictvím výchozí hodnoty zadané ve schématu, nebo ne. To je zveřejněný prostřednictvím <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
3.  Poznámky: Odkazy na schéma komponenty, které mohou být typ definice nebo deklarace prvků a atributů. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> obsahuje informace o konkrétním typu uzlu, pokud je platný. Pokud platnost uzel neznámý, například když se ověřila pak následně upravit. pak bude <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> je nastavena na `null` je stále k dispozici různé vlastnosti informací o typu, ale <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
 Následující příklad ukazuje, použijte informace v vystavené informační po Schema ověření sadu <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 V příkladu přebírá `books.xml` souboru jako vstup.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Tento příklad využívá taky `books.xsd` schématu jako vstup.  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"   
attributeFormDefault="unqualified" elementFormDefault="qualified"   
targetNamespace="http://www.contoso.com/books"   
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Získání zadaných hodnot pomocí vlastností ValueAs  
 Zadaná hodnota uzlu je možné načíst podle přístupu <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator>. V některých případech můžete převést hodnotu typu uzlu do jiného typu. Běžným příkladem je k získání číselné hodnoty z uzlu XML. Představte si třeba neověřený a netypové následujícího dokumentu XML.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Pokud <xref:System.Xml.XPath.XPathNavigator> je umístěn na `price` element <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> by být vlastnost `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> by být vlastnost <xref:System.String>a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnost bude řetězec `10.00`.  
  
 Je však stále možné extrahovat hodnotu jako číselnou hodnotu použití <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, nebo <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> metody a vlastnosti. Následující příklad ukazuje takový typu přetypování pomocí provádí <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
