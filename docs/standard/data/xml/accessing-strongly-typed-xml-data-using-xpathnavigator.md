---
title: Přístup k datům XML silného typu pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: 61957ff88ef57703aff1861238ee10b23c2f16ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291601"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Přístup k datům XML silného typu pomocí XPathNavigator
Jako instance datového modelu XPath 2,0 <xref:System.Xml.XPath.XPathNavigator> může třída obsahovat data silného typu, která se mapují na typy modulu CLR (Common Language Runtime). Podle datového modelu XPath 2,0 mohou pouze elementy a atributy obsahovat data silného typu. <xref:System.Xml.XPath.XPathNavigator>Třída poskytuje mechanismy pro přístup k datům v rámci <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo jako data silného typu a mechanismy pro převod z jednoho datového typu na jiný.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informace o typech vystavených pomocí XPathNavigator  
 Data XML 1,0 jsou technicky bez typu, pokud se nezpracovávají pomocí DTD, schématu definice jazyka XML (XSD) nebo jiného mechanismu. Existuje několik kategorií typů informací, které mohou být přidruženy k elementu nebo atributu XML.  
  
- Jednoduché typy CLR: žádné jazyky schématu XML nepodporují přímo typy modulu CLR (Common Language Runtime). Vzhledem k tomu, že je vhodné, aby bylo možné zobrazit jednoduchý element a obsah atributu jako nejvhodnější typ CLR, lze veškerý jednoduchý obsah zadat jako <xref:System.String> v případě nepřítomnosti informací o schématu pomocí jakýchkoli přidaných informací o schématu, který potenciálně může tento obsah snadno použít pro přesnější typ. Můžete najít nejlépe vyhovující typ CLR jednoduchého prvku a obsahu atributu pomocí <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> Vlastnosti. Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](type-support-in-the-system-xml-classes.md).  
  
- Seznamy jednoduchých typů (CLR): element nebo atribut s jednoduchým obsahem může obsahovat seznam hodnot oddělených prázdným znakem. Hodnoty jsou určeny schématem XML jako "typ seznamu". V případě absence schématu XML by takový jednoduchý obsah byl považován za jediný textový uzel. Pokud je k dispozici schéma XML, tento jednoduchý obsah může být vystaven jako řada atomických hodnot, z nichž každý má jednoduchý typ, který se mapuje na kolekci objektů CLR. Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](type-support-in-the-system-xml-classes.md).  
  
- Zadaná hodnota: atribut, který je ověřený schématem nebo element s jednoduchým typem, má zadanou hodnotu. Tato hodnota je primitivního typu, jako je číselná hodnota, řetězec nebo typ data. Všechny předdefinované jednoduché typy v XSD lze namapovat na typy CLR, které poskytují přístup k hodnotě uzlu jako vhodnější typ místo pouze jako <xref:System.String> . Element s atributy nebo podřízenými prvky je považován za komplexní typ. Zadaná hodnota komplexního typu s jednoduchým obsahem (pouze textové uzly jako podřízené položky) je stejná jako u jednoduchého typu jejího obsahu. Zadaná hodnota komplexního typu se složitým obsahem (jeden nebo více podřízených elementů) je řetězcová hodnota zřetězení všech podřízených textových uzlů vrácených jako <xref:System.String> . Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](type-support-in-the-system-xml-classes.md).  
  
- Název typu specifického pro jazyk schématu: ve většině případů jsou typy CLR, které jsou nastaveny jako vedlejší účinky použití externího schématu, použity k poskytnutí přístupu k hodnotě uzlu. Mohou však nastat situace, kdy budete chtít prostudovat typ přidružený ke konkrétnímu schématu použitému pro dokument XML. Například můžete chtít Hledat v dokumentu XML a extrahovat všechny prvky, které jsou určeny tak, aby měly obsah typu "PurchaseOrder" podle připojeného schématu. Tyto informace o typu lze nastavit pouze v důsledku ověřování schématu a k těmto informacím jsou přistupované prostřednictvím <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastností a <xref:System.Xml.XPath.XPathNavigator> třídy. Další informace najdete níže v části post PSVI (podrobnějšího ověření schématu).  
  
- Odraz typu specifického pro jazyk schématu: v jiných případech můžete chtít získat další podrobnosti o typu specifického pro schéma, který se použije pro dokument XML. Například při čtení souboru XML může být vhodné extrahovat `maxOccurs` atribut pro každý platný uzel v dokumentu XML, aby bylo možné provést nějaký vlastní výpočet. Vzhledem k tomu, že tyto informace jsou nastaveny pouze pomocí ověřování schématu, jsou k ní přistupované prostřednictvím <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy. Další informace najdete níže v části post PSVI (podrobnějšího ověření schématu).  
  
## <a name="xpathnavigator-typed-accessors"></a>Přistupující objekty XPathNavigator typovaného typu  
 V následující tabulce jsou uvedeny různé vlastnosti a metody <xref:System.Xml.XPath.XPathNavigator> třídy, které lze použít pro přístup k informacím o typu uzlu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Obsahuje informace o typu schématu XML pro uzel, pokud je platný.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Obsahuje informační sadu po ověření schématu uzlu, který se přidá po ověření. To zahrnuje informace o typu schématu XML a také informace o platnosti.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Typ CLR typové hodnoty uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Obsah uzlu jako jednu nebo více hodnot CLR, jejichž typ je co nejblíže typu schématu XML uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String>Hodnota aktuálního uzlu přetypování na <xref:System.Boolean> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:boolean` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String>Hodnota aktuálního uzlu přetypování na <xref:System.DateTime> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:datetime` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String>Hodnota aktuálního uzlu přetypování na <xref:System.Double> hodnotu podle pravidel přetypování XPath 2,0 pro `xsd:double` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String>Hodnota aktuálního uzlu přetypování na <xref:System.Int32> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:integer` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String>Hodnota aktuálního uzlu přetypování na <xref:System.Int64> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:integer` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Obsah přetypování uzlu na cílový typ podle pravidel přetypování XPath 2,0.|  
  
 Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Informační sada po ověření schématu (PSVI)  
 Procesor schématu XML přijímá jako vstup XML informační sadu a převede je do informační sady po ověření schématu (PSVI). PSVI je původní vstupní informační sada XML s přidanými novými informacemi a novými vlastnostmi přidanými k existujícím položkám informací. Do informační sady XML v PSVI jsou přidány tři široké třídy informací, které jsou zpřístupněny v <xref:System.Xml.XPath.XPathNavigator> .  
  
1. Výsledky ověření: informace o tom, zda byl prvek nebo atribut úspěšně ověřen nebo nikoli. Tato vlastnost je vystavena <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
2. Výchozí informace: označení, zda byla hodnota elementu nebo atributu získána prostřednictvím výchozích hodnot zadaných ve schématu nebo nikoli. Tato vlastnost je vystavena <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
3. Anotace typu: odkazy na komponenty schématu, které mohou být definice typu nebo deklarace element a atributu. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A>Vlastnost <xref:System.Xml.XPath.XPathNavigator> obsahuje konkrétní informace o typu uzlu, pokud je platný. Pokud je platnost uzlu neznámá, například při ověření, následně upraveno. pak <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> je vlastnost nastavena na, `null` ale informace o typu jsou stále k dispozici z různých vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
 Následující příklad znázorňuje použití informací v informačním okně po ověření schématu vystaveném pomocí <xref:System.Xml.XPath.XPathNavigator> .  
  
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
  
 Příklad přebírá `books.xml` soubor jako vstup.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Příklad také převezme `books.xsd` schéma jako vstup.  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Získání typových hodnot pomocí vlastností ValueAs  
 Zadanou hodnotu uzlu lze načíst přístupem k <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> . V některých případech je vhodné převést typovou hodnotu uzlu na jiný typ. Běžným příkladem je získání číselné hodnoty z uzlu XML. Zvažte například následující neověřený a Netypový dokument XML.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Pokud <xref:System.Xml.XPath.XPathNavigator> je umístěn na elementu, vlastnost by měla být a vlastnost by měla být `price` <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> `null` <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> <xref:System.String> <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> řetězec `10.00` .  
  
 Je však možné i nadále extrahovat hodnotu jako číselnou hodnotu pomocí <xref:System.Xml.XPath.XPathItem.ValueAs%2A> <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A> metod,, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> nebo <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> a vlastností. Následující příklad ilustruje provádění takového přetypování pomocí <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.  
  
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
  
 Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Podpora typu v třídách System.Xml](type-support-in-the-system-xml-classes.md)
- [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)
- [Navigace v sadě uzlů pomocí XPathNavigator](node-set-navigation-using-xpathnavigator.md)
- [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Extrahování dat XML pomocí XPathNavigator](extract-xml-data-using-xpathnavigator.md)
