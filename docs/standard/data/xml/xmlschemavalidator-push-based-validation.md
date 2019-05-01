---
title: Přímé ověření XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d1d5602ff224c1c8f3e0948fc93c9200b9661e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026806"
---
# <a name="xmlschemavalidator-push-based-validation"></a>Přímé ověření XmlSchemaValidator
<xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje mechanismus efektivního, vysoce výkonné ověřit data XML oproti schémat XML v podobě nabízené. Například <xref:System.Xml.Schema.XmlSchemaValidator> třída umožňuje ověřit XML informační sadu místní bez nutnosti ho serializovat jako dokument XML a potom změny zpracování dokumentu pomocí ověřování čtecí modul XML.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třída může být použita v pokročilých scénářích, jako je například vytváření modulů ověřování přes vlastní zdroje dat XML nebo jako způsob, jak sestavit ověřování zapisovače XML.  
  
 Následuje příklad použití <xref:System.Xml.Schema.XmlSchemaValidator> třídy k ověření `contosoBooks.xml` souboru proti `contosoBooks.xsd` schématu. V příkladu se používá <xref:System.Xml.Serialization.XmlSerializer> třídy k deserializaci `contosoBooks.xml` souboru a předat hodnotu uzly do metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy.  
  
> [!NOTE]
>  V tomto příkladu se používají v částech tohoto tématu.  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 V příkladu přebírá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad využívá taky `contosoBooks.xsd` jako vstup.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="bookstore">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element maxOccurs="unbounded" name="book">  
                    <xs:complexType>  
                        <xs:sequence>  
                            <xs:element name="title" type="xs:string" />  
                            <xs:element name="author">  
                                <xs:complexType>  
                                    <xs:sequence>  
                                        <xs:element minOccurs="0" name="name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />  
                                    </xs:sequence>  
                                </xs:complexType>  
                            </xs:element>  
                            <xs:element name="price" type="xs:decimal" />  
                        </xs:sequence>  
                        <xs:attribute name="genre" type="xs:string" use="required" />  
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />  
                        <xs:attribute name="ISBN" type="xs:string" use="required" />  
                    </xs:complexType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a>Ověřování dat XML pomocí XmlSchemaValidator  
 Pokud chcete začít, ověřování informační sadu XML, musí nejprve inicializovat novou instanci třídy <xref:System.Xml.Schema.XmlSchemaValidator> pomocí <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Přebírá konstruktor <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, a <xref:System.Xml.XmlNamespaceManager> objektů jako parametry a také <xref:System.Xml.Schema.XmlSchemaValidationFlags> hodnotu jako parametr. <xref:System.Xml.XmlNameTable> Objektu se používá k atomizovat dobře známé obor názvů řetězce jako obor názvů schématu, obor názvů XML a tak dále a je předán <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metoda při ověřování jednoduchý obsah. <xref:System.Xml.Schema.XmlSchemaSet> Objekt obsahuje schémata XML používaná k ověření informační sadu XML. <xref:System.Xml.XmlNamespaceManager> Objektu se používá k překladu názvů při ověřování došlo k. <xref:System.Xml.Schema.XmlSchemaValidationFlags> Hodnota slouží k zakázání určitých funkcí ověření.  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
### <a name="initializing-validation"></a>Inicializuje se ověření  
 Po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen, existují dvě přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody použité k inicializaci stav <xref:System.Xml.Schema.XmlSchemaValidator> objektu. Tady jsou dva <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 Výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu na jeho počáteční stav a přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu počáteční stav pro částečné ověření.  
  
 Obě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody lze volat pouze ihned po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen nebo po volání <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.  
  
 Příklad <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metodou, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
#### <a name="partial-validation"></a>Částečné ověřování  
 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu počáteční stav pro částečné ověřování.  
  
 V následujícím příkladu <xref:System.Xml.Schema.XmlSchemaObject> je inicializován pro částečné ověřování pomocí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody. `orderNumber` Element schématu je předán tak, že vyberete element schématu pomocí <xref:System.Xml.XmlQualifiedName> v <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekci vrácené poskytovatelem <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> objektu. <xref:System.Xml.Schema.XmlSchemaValidator> Objekt pak ověří tato konkrétní elementu.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add(Nothing, "schema.xsd")  
schemaSet.Compile()  
Dim nameTable As NameTable = New NameTable()  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
  
Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)  
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))  
  
validator.ValidateElement("orderNumber", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateText("123")  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
schemaSet.Compile();  
NameTable nameTable = new NameTable();  
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);  
  
validator.ValidateElement("orderNumber", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateText("123");  
validator.ValidateEndElement(null);  
```  
  
 Příklad vezme jako vstupní údaje následujícího schématu XML.  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
### <a name="adding-additional-schemas"></a>Přidat další schémata  
 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metodu <xref:System.Xml.Schema.XmlSchemaValidator> třída se používá k přidání schématu XML na sadu při ověřování se používají schémata. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda umožňuje simulovat účinek zjištění vložené schéma XML v informační sadu XML, které se ověřují.  
  
> [!NOTE]
>  Cílový obor názvů <xref:System.Xml.Schema.XmlSchema> parametr se nemůže shodovat, který všechny elementu nebo atributu už, se kterými <xref:System.Xml.Schema.XmlSchemaValidator> objektu.  
>   
>  Pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> hodnotu nebyl předán jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda nemá žádný účinek.  
  
 Výsledkem <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda je závislé na aktuálním kontextu uzlu XML ověřován. Další informace o ověření kontextů najdete v části "Ověření kontextu" tohoto tématu.  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
### <a name="validating-elements-attributes-and-content"></a>Ověřování elementů, atributů a obsahu  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje několik metod, které slouží k ověření elementů, atributů a obsahu v informační sadu XML pomocí schémat XML. Následující tabulka popisuje každý z těchto metod.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Ověří název elementu v aktuálním kontextu.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Ověří atributů v rámci aktuálního kontextu elementu nebo proti <xref:System.Xml.Schema.XmlSchemaAttribute> objekt předán jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Ověří, zda všechny povinné atributy v kontextu elementu jsou k dispozici a připraví <xref:System.Xml.Schema.XmlSchemaValidator> pro ověření podřízený obsah elementu.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Ověřuje, zda je povolen v rámci aktuálního kontextu elementu textu a shromažďuje text pro ověření, pokud je aktuální prvek má jednoduchý obsah.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Ověřuje, zda je prázdné místo je povolen v rámci aktuálního kontextu elementu a shromažďuje mezer pro ověření, zda aktuální prvek má jednoduchý obsah.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Ověří, zda textový obsah elementu, který je platný podle jeho datového typu pro prvky s jednoduchým obsahem a ověří, zda je obsah aktuální prvek kompletní pro elementy se složitým obsahem.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Přeskočí ověření aktuální obsah elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objektu na ověřování obsahu v rámci nadřazeného elementu.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Ukončí ověření a zkontroluje omezení identity pro celý dokument XML, pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> je nastavena možnost ověřování.|  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaValidator> Třída má definovaný stavu přechodu, který vynucuje pořadí a výskyt volání na každý z metod popsaných v předchozí tabulce. Přechod určitý stav <xref:System.Xml.Schema.XmlSchemaValidator> třídy je popsaný v části "XmlSchemaValidator přechod stavu" v tomto tématu.  
  
 Příklad metody použité k ověření elementů, atributů a obsahu v informační sadu XML podívejte se na příklad v předchozím oddílu. Další informace o těchto metodách v tématu <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a>Ověřování obsahu pomocí XmlValueGetter  
 <xref:System.Xml.Schema.XmlValueGetter> `delegate` Je možné předat hodnotu atributu, text nebo prázdný znak uzlů jako typy Common Language Runtime (CLR) kompatibilní s typem jazyka pro definici schématu XML (XSD) atribut, text nebo uzel prázdné znaky. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Je užitečné, pokud CLR hodnotu atributu, text nebo uzel prázdné místo je již k dispozici a zabraňuje převodu na náklady `string` a pak ho znovu reparsing pro ověření.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, A <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> metody jsou přetížené a přijmout hodnotu atributu, text nebo prázdný znak uzlů jako `string` nebo <xref:System.Xml.Schema.XmlValueGetter> `delegate`.  
  
 Tyto metody <xref:System.Xml.Schema.XmlSchemaValidator> přijmout třídy <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 Tady je příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate` z <xref:System.Xml.Schema.XmlSchemaValidator> úvodním příkladem třídu. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Vrátí hodnotu jako atribut <xref:System.DateTime> objektu. Chcete-li to ověřit <xref:System.DateTime> objekt vrácený <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> objekt nejprve převeden na typ hodnoty (ValueType je výchozí mapování modulu CLR pro typ XSD) pro datový typ atributu a kontroly omezující vlastnosti na převedenou hodnotu hodnota.  
  
```vb  
Shared dateTimeGetterContent As Object  
  
Shared Function dateTimeGetterHandle() As Object  
    Return dateTimeGetterContent  
End Function  
  
Shared Function dateTimeGetter(ByVal dateTime As DateTime) As XmlValueGetter  
    dateTimeGetterContent = dateTime  
    Return New XmlValueGetter(AddressOf dateTimeGetterHandle)  
End Function  
```  
  
```csharp  
static object dateTimeGetterContent;  
  
static object dateTimeGetterHandle()  
{  
    return dateTimeGetterContent;  
}  
  
static XmlValueGetter dateTimeGetter(DateTime dateTime)  
{  
    dateTimeGetterContent = dateTime;  
    return new XmlValueGetter(dateTimeGetterHandle);  
}  
```  
  
 Kompletní příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate`, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlValueGetter> `delegate`, najdete v článku <xref:System.Xml.Schema.XmlValueGetter>, a <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
#### <a name="post-schema-validation-information"></a>Po-Schema--informace o ověřování  
 <xref:System.Xml.Schema.XmlSchemaInfo> Třída představuje některé po-Schema-ověření – informace o uzlu XML ověřen <xref:System.Xml.Schema.XmlSchemaValidator> třídy. Různé metody <xref:System.Xml.Schema.XmlSchemaValidator> přijmout třídy <xref:System.Xml.Schema.XmlSchemaInfo> objektu jako volitelný, (`null`) `out` parametru.  
  
 Po úspěšném ověření, vlastnosti <xref:System.Xml.Schema.XmlSchemaInfo> objektu se nastavují s výsledky ověření. Například po úspěšném ověření pomocí atributu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> objektu uživatele (Pokud je zadaný) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> s výsledky ověření jsou nastaveny vlastnosti .  
  
 Následující <xref:System.Xml.Schema.XmlSchemaValidator> přijmout metody třídy <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako výstupní parametr.  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 Kompletní příklad <xref:System.Xml.Schema.XmlSchemaInfo> třídy, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaInfo> najdete v tématu <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci.  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Načítání očekávané částice, atributy a neurčené výchozí atributy  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody pro načtení očekávané částice, atributy a neurčené výchozí atributy v aktuálním kontextu ověřování.  
  
#### <a name="retrieving-expected-particles"></a>Načítání očekávané částice  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaParticle> objekty, které obsahují očekávané částice v rámci aktuálního kontextu elementu. Platný částice, které může být vrácen <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody jsou instance <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAny> třídy.  
  
 Když složku pro obsahový model je `xs:sequence`, je vrácen pouze další částice v sekvenci. Pokud je složku pro model obsahu `xs:all` nebo `xs:choice`, pak jsou vráceny všechny platné částice, které byste mohli provést, v rámci aktuálního kontextu elementu.  
  
> [!NOTE]
>  Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána ihned po volání <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí všechny globální prvky.  
  
 Například v schématu XML definice jazyk (XSD) schématu a XML dokumentů, které následují po ověření `book` elementu, `book` element je aktuálního kontextu elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt představující `title` elementu. Pokud je kontext ověřování `title` elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí prázdné pole. Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `title` element ověřily ale předtím, než `description` element byl ověřen, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt představující `description` elementu. Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `description` element byl ověřen a vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaAny> objekt představující zástupný znak.  
  
```vb  
Dim reader As XmlReader =  XmlReader.Create("input.xml")   
  
Dim schemaSet As XmlSchemaSet =  New XmlSchemaSet()   
schemaSet.Add(Nothing, "schema.xsd")  
Dim manager As XmlNamespaceManager =  New XmlNamespaceManager(reader.NameTable)   
  
Dim validator As XmlSchemaValidator =  New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)  
validator.Initialize()  
  
validator.ValidateElement("book", "", Nothing)  
  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("title", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
validator.ValidateEndElement(Nothing)  
  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("description", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()  
    Console.WriteLine(particle.GetType())  
Next  
  
validator.ValidateElement("namespace", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlReader reader = XmlReader.Create("input.xml");  
  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
XmlNamespaceManager manager = new XmlNamespaceManager(reader.NameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize();  
  
validator.ValidateElement("book", "", null);  
  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("title", "", null);  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("description", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())  
{  
    Console.WriteLine(particle.GetType());  
}  
  
validator.ValidateElement("namespace", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
validator.ValidateEndElement(null);  
```  
  
 Příklad vezme jako vstupní údaje následující kód XML.  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 Příklad vezme jako vstupní údaje následující schéma XSD.  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídě jsou závislé na aktuálním kontextu se ověřují. Další informace najdete v části "Ověření kontextu" tohoto tématu.  
  
 Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodou, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
#### <a name="retrieving-expected-attributes"></a>Načítání očekávané atributy  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaAttribute> objekty, které obsahují očekávané atributy v rámci aktuálního kontextu elementu.  
  
 Například v příkladu v úvodu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda se používá k načtení všech atributů `book` element.  
  
 Při volání <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda ihned po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metody, jsou vráceny všechny atributy, které mohou být zobrazeny v dokumentu XML. Ale při volání <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> za jeden nebo více volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody, jsou vráceny atributy, které ještě neověřily aktuálního elementu.  
  
> [!NOTE]
>  Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídě jsou závislé na aktuálním kontextu se ověřují. Další informace najdete v části "Ověření kontextu" tohoto tématu.  
  
 Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodou, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
#### <a name="retrieving-unspecified-default-attributes"></a>Načítání neurčené výchozí atributy  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda naplní <xref:System.Collections.ArrayList> zadaným <xref:System.Xml.Schema.XmlSchemaAttribute> objekty pro atributy s výchozími hodnotami, které nebyly ověřené dříve pomocí <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody v kontextu elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla být volána po volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metodu na jednotlivé atributy v kontextu elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla sloužit k určení výchozí atributy jsou má být vložen do dokumentu XML, který je ověřován.  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.  
  
### <a name="handling-schema-validation-events"></a>Zpracování událostí ověření schématu  
 Schéma ověření upozornění a chyb zjištěných při ověřování jsou zpracovávány <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> událost <xref:System.Xml.Schema.XmlSchemaValidator> třídy.  
  
 Schéma ověření upozornění mají <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>. Pokud ne <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> byla přiřazena, <xref:System.Xml.Schema.XmlSchemaValidationException> všechny chyby ověřování schématu s, je vyvolána <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>. Však <xref:System.Xml.Schema.XmlSchemaValidationException> není vyvolána pro upozornění při ověřování schématu s <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning>.  
  
 Následující je příklad <xref:System.Xml.Schema.ValidationEventHandler> , která obdrží upozornění při ověřování schématu a chyb při ověřování schématu z úvodním příkladem.  
  
```vb  
Shared Sub SchemaValidationEventHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
    Select Case e.Severity  
        Case XmlSeverityType.Error  
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)  
            Exit Sub  
        Case XmlSeverityType.Warning  
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)  
            Exit Sub  
    End Select  
End Sub  
```  
  
```csharp  
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)  
{  
    switch (e.Severity)  
    {  
        case XmlSeverityType.Error:  
            Console.WriteLine("\nError: {0}", e.Message);  
            break;  
        case XmlSeverityType.Warning:  
            Console.WriteLine("\nWarning: {0}", e.Message);  
            break;  
    }  
}  
```  
  
 Kompletní příklad <xref:System.Xml.Schema.ValidationEventHandler>, podívejte se na příklad v úvodu. Další informace najdete v tématu <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci.  
  
## <a name="xmlschemavalidator-state-transition"></a>Přechod stavu XmlSchemaValidator  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třída má definovaný stavu přechodu, který vynucuje pořadí a výskyt volání na jednotlivé metody použité k ověření elementů, atributů a obsahu v informační sadu XML.  
  
 Následující tabulka popisuje přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy a pořadí a výskyt volání metody, které mohou být provedeny v jednotlivých stavech.  
  
|Stav|Přechod|  
|-----------|----------------|  
|Ověření|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|  
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; – Element|  
|Prvek|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;|  
|Obsah|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; – Element|  
  
> [!NOTE]
>  <xref:System.InvalidOperationException> Je vyvolána každou z metod uvedených v tabulce výše, při volání metody se provádí v nesprávné pořadí podle aktuálního stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.  
  
 Výše uvedené tabulce přechodu stavu pomocí interpunkčních znamének jsou popsány metody a ostatní stavy, které lze volat pro každý stav přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy. Symboly použité jsou stejné symboly součástí reference na standardy XML pro definici typu dokumentu (DTD).  
  
 Následující tabulka popisuje vlivu metody interpunkčních znamének v předchozí tabulce přechod stavu a ostatní stavy, které lze volat pro každý stav ve stavu přechodu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.  
  
|Symbol|Popis|  
|------------|-----------------|  
|&#124;|Je možné volat metodu nebo stavu (jeden před panelu) nebo jedna po ní.|  
|?|Metoda a stav, který předchází otazník je volitelný, ale pokud je volána jej lze volat pouze jednou.|  
|*|Metoda nebo stav, který předchází * symbol je volitelný a může být volána více než jednou.|  
  
## <a name="validation-context"></a>Kontext ověřování  
 Metody <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření elementů, atributů a obsahu v informační sadu XML, změňte kontext ověřování ze <xref:System.Xml.Schema.XmlSchemaValidator> objektu. Například <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> metoda přeskočí ověření aktuální obsah elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objektu na ověřování obsahu v rámci nadřazeného elementu; je ekvivalentní k přeskočení ověření pro všechny podřízené objekty aktuálního elementu a následným voláním <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.  
  
 Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídě jsou závislé na aktuálním kontextu se ověřují.  
  
 Následující tabulka popisuje výsledky volání těchto metod po volání jedné z metod <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření elementů, atributů a obsahu v informační sadu XML.  
  
|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pole obsahující všechny globální prvky.<br /><br /> Pokud přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr je volána k inicializaci částečné ověřování elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.|Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> Pokud přetížení <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr je volána k inicializaci částečné ověřování atributu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut ke kterému <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.|Přidá schématu tak <xref:System.Xml.Schema.XmlSchemaSet> z <xref:System.Xml.Schema.XmlSchemaValidator> objektu, pokud ho neobsahuje žádné chyby během předběžného zpracování.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Pokud je platný, element kontextu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekáván jako podřízené položky elementu kontextu.<br /><br /> Pokud není platný, element kontextu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.|Pokud element kontextu je platný a pokud bez volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> bylo dříve vytvořeno <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam všech atributů definovaných v kontextu elementu.<br /><br /> Pokud některé atributy již byly ověřeny, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam hodnot zbývajících atributy, které mají být ověřen.<br /><br /> Pokud není platný, element kontextu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Pokud atribut kontextu je atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekává jako první podřízený element kontextu.|Pokud atribut kontextu je atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývající atributů má být ověřen.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí sekvenci prvků očekává jako první podřízený element kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí seznam povinných a volitelných atributů, které se ještě na ověření pro element kontextu.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí sekvenci prvků očekává jako první podřízený element kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí prázdné pole.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Pokud element kontextu contentType je kombinovat, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekává na další pozici.<br /><br /> Pokud element kontextu contentType je typu TextOnly nebo je prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> Pokud element kontextu contentType je ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekáván na další pozici, ale k chybě ověřování již došlo.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí element kontextu seznam atributů nebyl ověřen.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Pokud prázdnému kontextu je nejvyšší úrovně prázdných <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Pokud prázdnému kontextu je nejvyšší úrovně prázdných <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí sekvenci prvků po elementu kontextu (je to možné na stejné úrovni).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí element kontextu seznam atributů nebyl ověřen.<br /><br /> Pokud element kontextu nemá žádný nadřazený objekt pak <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdný seznam (element kontextu je nadřazeného člena aktuální prvek, na který <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> byla volána).|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Vrátí prázdné pole.|Vrátí prázdné pole.|Stejné jako výše.|  
  
> [!NOTE]
>  Hodnoty vrácené různé vlastnosti objektu <xref:System.Xml.Schema.XmlSchemaValidator> třídy se nezmění voláním některé z metod ve výše uvedené tabulky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Schema.XmlSchemaValidator>
