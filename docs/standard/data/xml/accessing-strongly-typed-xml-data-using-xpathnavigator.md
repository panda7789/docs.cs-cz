---
title: "Přístup k důrazně zadali pomocí objektem XPathNavigator nastaveným na Data XML"
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
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61c78adff541ac2ba261d31776478a0468e21d4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Přístup k důrazně zadali pomocí objektem XPathNavigator nastaveným na Data XML
Jako instance datového modelu XPath 2.0 <xref:System.Xml.XPath.XPathNavigator> třídy může obsahovat data silného typu, který se mapuje na běžné typy language runtime (CLR). Podle modelu dat XPath 2.0 může obsahovat pouze elementy a atributy data silného typu. <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje mechanismus pro přístup k datům v rámci <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> jako silného typu dat, jakož i mechanismy pro převod z jednoho datového typu na jiný objekt.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informace o typu vystavené objektem XPathNavigator nastaveným na  
 Data XML 1.0 je technicky bez typu, pokud zpracování s DTD, XML schéma definition language (XSD) schématu nebo jinému kontrolnímu mechanismu. Existuje několik kategorií informace o typu, který může být přidružen elementu XML nebo atributu.  
  
-   Jednoduché typy CLR: Žádný z jazyků schématu XML nepodporuje typy Common Language Runtime (CLR) přímo. Protože je užitečné, abyste mohli zobrazit jednoduché elementu a atributu obsah jako nejvhodnější typ CLR, všechny jednoduchým obsahem lze zadat jako <xref:System.String> chybí informace o schématu s žádným přidat informace o schématu potenciálně upřesnění tomuto obsahu uživateli více příslušného typu. Můžete najít nejlépe odpovídající typ CLR jednoduchým obsahem elementu a atributu pomocí <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> vlastnost. Další informace o mapování z předdefinovaných typů schématu pro typy CLR najdete v tématu [podpora typu ve třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Seznam typů jednoduché (CLR): elementu nebo atributu s jednoduchým obsahem může obsahovat seznam hodnot oddělených mezer. Hodnoty jsou určené schéma XML jako "typ seznamu". Chybí schématu XML by takové jednoduchým obsahem považovány za jeden textový uzel. Pokud schéma XML je k dispozici, mohou být zpřístupněny tento jednoduchý obsah jako řadu atomic hodnoty, každý s jednoduchý typ, který se mapuje na kolekce objektů CLR. Další informace o mapování z předdefinovaných typů schématu pro typy CLR najdete v tématu [podpora typu ve třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Zadaná hodnota: Ověřit schéma atribut nebo element s jednoduchého typu obsahuje hodnotu typu. Tato hodnota je primitivní typ, například číselný, řetězce nebo typ datum. Všechny předdefinované jednoduché typy v XSD lze mapovat na typy CLR, které poskytují přístup k hodnotě uzlu jako typ vhodnější místo stejně jako <xref:System.String>. Element s atributy nebo podřízené položky elementu se považuje za komplexního typu. Typové hodnotu pro komplexní typ s jednoduchým obsahem (pouze textové uzly jako podřízené objekty) je stejný jako u jednoduchý typ část jeho obsahu. Hodnota typu komplexního typu se složitým obsahem (jeden nebo více podřízených prvků) je s řetězcovou hodnotou obsahující zřetězení všechny jeho podřízené textové uzly vrátí jako <xref:System.String>. Další informace o mapování z předdefinovaných typů schématu pro typy CLR najdete v tématu [podpora typu ve třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Schématu jazyk konkrétní název typu: Ve většině případů typů CLR, které jsou nastavené jako vedlejší účinek použití externí schéma, slouží k poskytování přístupu k hodnotě uzlu. Mohou však nastat situace, místo zkontrolujte typ spojený s konkrétní schématu použitého pro dokument XML. Například můžete chtít hledání v dokumentu XML extrahování všechny elementy, které jsou určeny tak, aby měl obsah typu "PurchaseOrder" podle připojeného schématu. Tyto informace o typu lze nastavit pouze v důsledku ověřování schématu a tyto informace je přístupné přes <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> a <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy. Další informace najdete v části informační Post schématu ověření sadu (PSVI) níže.  
  
-   Reflexe konkrétní jazyk schématu: V ostatních případech můžete chtít získat další podrobnosti o konkrétní schématu typu u dokumentu XML. Například při čtení souboru XML, můžete k extrakci `maxOccurs` atribut pro každý uzel platný v dokumentu XML tak, aby bylo možné provést některé vlastní výpočet. Protože tyto informace je nastavena pouze prostřednictvím ověřování schématu, je přístupné přes <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy. Další informace najdete v části informační Post schématu ověření sadu (PSVI) níže.  
  
## <a name="xpathnavigator-typed-accessors"></a>Objektem XPathNavigator nastaveným na silné přístupové objekty  
 Následující tabulka uvádí různé vlastnosti a metody <xref:System.Xml.XPath.XPathNavigator> třídu, která lze použít pro přístup k informacím typ o uzlu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Pokud je platná tato položka obsahuje informace o uzlu typ schématu XML.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Tato položka obsahuje informační Post schématu ověření sadu uzlu, který bude přidán za ověření. To zahrnuje informace o typu schématu XML a také informace platnosti.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Typ CLR typové hodnotu uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Obsah uzlu CLR jeden nebo více hodnot s typem je nejvíce odpovídá typ schématu XML uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String> Hodnotu aktuální uzel přetypovat <xref:System.Boolean> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String> Hodnotu aktuální uzel přetypovat <xref:System.DateTime> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String> Hodnotu aktuální uzel přetypovat <xref:System.Double> hodnoty, podle pravidla přetypování XPath 2.0 pro `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String> Hodnotu aktuální uzel přetypovat <xref:System.Int32> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String> Hodnotu aktuální uzel přetypovat <xref:System.Int64> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Obsah uzlu přetypovat na typ cíle podle pravidel přetypování XPath 2.0.|  
  
 Další informace o mapování z předdefinovaných typů schématu pro typy CLR najdete v tématu [podpora typu ve třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Informační Post schématu ověření sadu (PSVI)  
 Procesor schématu XML přijímá informační sadu XML jako vstup a převede jej do schématu ověření informační sadu (PSVI Post). PSVI je původní vstupní XML informační sadu s přidat nové informace položky a nové vlastnosti, které jsou přidány do existujících položek informace. Existují tři obecné třídy informací zapisovaných do informační sadu XML v PSVI, které jsou vystavené <xref:System.Xml.XPath.XPathNavigator>.  
  
1.  Ověření výstupy: Informace o tom, jestli elementu nebo atributu byl úspěšně ověřen nebo ne. To je zveřejněný prostřednictvím <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
2.  Informace o výchozí: Označení, zda hodnota elementu nebo atributu byl získán prostřednictvím výchozí hodnoty zadané ve schématu, nebo ne. To je zveřejněný prostřednictvím <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
3.  Typ poznámky: Odkazy na komponenty schématu, které mohou být definic typů nebo elementu a atributu deklarace. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> obsahuje informace o konkrétní typ uzlu, pokud je platná. Pokud platnost uzel neznámý, například když se ověřila pak následně upravit. pak se <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> je nastavena na `null` , ale stále k dispozici v různé vlastnosti informací o typu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
 Následující příklad ilustruje, pomocí informací v vystavené informační Post schématu ověření sadu <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
 V příkladu trvá `books.xml` souboru jako vstup.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Tento příklad také trvá `books.xsd` schématu jako vstup.  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Získat zadávaných hodnot pomocí vlastnosti ValueAs  
 Hodnota typu uzlu může načíst přístup k <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator>. V některých případech můžete chtít převést hodnotu typu uzlu na jiný typ. Běžným příkladem jsou k získání číselné hodnoty z uzlu XML. Zvažte například následující neověřený a bez typu dokumentu XML.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Pokud <xref:System.Xml.XPath.XPathNavigator> je umístěn na `price` element <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> by vlastnost `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> by vlastnost <xref:System.String>a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnost bude řetězec `10.00`.  
  
 Je však stále možné rozbalte hodnotu jako číselná hodnota pomocí <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, nebo <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> metody a vlastnosti. Následující příklad ilustruje, provádění takových přetypování pomocí <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metoda.  
  
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
  
 Další informace o mapování z předdefinovaných typů schématu pro typy CLR najdete v tématu [podpora typu ve třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Podpora typu v System.Xml třídy](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 [Zpracování kódu XML dat pomocí jazyka XPath datový Model](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Uzel navigační sady pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Extrahovat pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
