---
title: "Ověření nabízené XmlSchemaValidator"
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
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60c2effea612a579b4c66b7c30243b785b86a263
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemavalidator-push-based-validation"></a>Ověření nabízené XmlSchemaValidator
<xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje mechanismus efektivní, vysoce výkonných ověřit data XML oproti schémat XML způsobem nabízené. Například <xref:System.Xml.Schema.XmlSchemaValidator> třída umožňuje ověřit XML informační sadu místní bez nutnosti serializovat jako dokument XML a pak rozboru dokument pomocí ověřování čtečky XML.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třídu lze použít v pokročilých scénářích, jako je například vytváření modulů ověření přes vlastní zdroje dat XML nebo jako způsob, jak sestavit ověřování zapisovače XML.  
  
 Následuje příklad použití <xref:System.Xml.Schema.XmlSchemaValidator> třída k ověření `contosoBooks.xml` souboru proti `contosoBooks.xsd` schématu. V příkladu se používá <xref:System.Xml.Serialization.XmlSerializer> třída k deserializaci `contosoBooks.xml` souborů a předat hodnotu uzlů do metody <xref:System.Xml.Schema.XmlSchemaValidator> – třída.  
  
> [!NOTE]
>  V tomto příkladu se používá napříč částech tohoto tématu.  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad také trvá `contosoBooks.xsd` jako vstup.  
  
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
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a>Ověřování pomocí XmlSchemaValidator dat XML  
 Pokud chcete začít, ověřování informační sadu XML, musí nejprve inicializovat novou instanci třídy <xref:System.Xml.Schema.XmlSchemaValidator> pomocí <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktor.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Konstruktor přijímá <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, a <xref:System.Xml.XmlNamespaceManager> objektů jako parametry a také <xref:System.Xml.Schema.XmlSchemaValidationFlags> hodnotu jako parametr. <xref:System.Xml.XmlNameTable> Objekt se používá k atomizovat dobře známé obor názvů řetězce jako obor názvů schématu, obor názvů XML a tak dále a je předána <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metoda při ověřování jednoduchý obsah. <xref:System.Xml.Schema.XmlSchemaSet> Objekt obsahuje schémat XML použitý k ověření informační sadu XML. <xref:System.Xml.XmlNamespaceManager> Objekt se používá k překladu při ověřování došlo k obory názvů. <xref:System.Xml.Schema.XmlSchemaValidationFlags> Hodnota se používá k zakázání určitých funkcí ověření.  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
### <a name="initializing-validation"></a>Inicializace ověření  
 Po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen, jsou uvedeny dvě přetížený <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody použité k inicializaci stav <xref:System.Xml.Schema.XmlSchemaValidator> objektu. Následují dva <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 Výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu a jeho počáteční stav přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, která použije <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt počáteční stav pro částečné ověření.  
  
 Obě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody lze volat pouze ihned po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen nebo po volání <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.  
  
 Příklad <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
#### <a name="partial-validation"></a>Částečné ověřování  
 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metody, která použije <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt počáteční stav pro částečné ověření.  
  
 V následujícím příkladu se <xref:System.Xml.Schema.XmlSchemaObject> inicializovaná pro částečné ověření pomocí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda. `orderNumber` Je předán element s schématu výběrem element schema podle <xref:System.Xml.XmlQualifiedName> v <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekce vrácené <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> objektu. <xref:System.Xml.Schema.XmlSchemaValidator> Objekt pak ověří tento konkrétní element.  
  
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
  
 V příkladu vezme jako vstupní následující schématu XML.  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
### <a name="adding-additional-schemas"></a>Přidání další schémata  
 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metodu <xref:System.Xml.Schema.XmlSchemaValidator> třída se používá pro přidání do sadu schémata používají při ověřování schématu XML. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda slouží k simulovat účinek zjištění schématu XML vložené v XML informační sadu, která je ověřována.  
  
> [!NOTE]
>  Cílový obor názvů <xref:System.Xml.Schema.XmlSchema> parametr nesmí odpovídat žádné elementu nebo atributu již, se kterými <xref:System.Xml.Schema.XmlSchemaValidator> objektu.  
>   
>  Pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> hodnota nebyl předán jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda neprovede žádnou akci.  
  
 Výsledkem <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda je závislé na aktuální kontext uzlu XML během ověřování. Další informace o ověření kontexty najdete v části "Ověření kontextu" v tomto tématu.  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
### <a name="validating-elements-attributes-and-content"></a>Ověřování prvky, atributy a obsahu  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje několik metod, které slouží k ověření prvky, atributy a obsah informační sadu XML pomocí schémat XML. Následující tabulka popisuje každý z těchto metod.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Ověří název elementu v aktuálním kontextu.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Ověří atribut v aktuálním kontextu element nebo proti <xref:System.Xml.Schema.XmlSchemaAttribute> objekt předaný jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Ověřuje, zda všechny povinné atributy v kontextu elementu jsou prezentovat a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt, který chcete ověřit obsah podřízeného prvku.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Ověří, zda je povolen v aktuálním kontextu element text a shromažďuje text pro ověření, pokud aktuálního elementu jednoduchý obsah.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Ověří, zda je povolen v aktuálním kontextu element prázdný a shromažďuje mezer pro ověření, zda má aktuálního elementu jednoduchý obsah.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Ověřuje, zda je platná podle jeho datového typu u elementů s jednoduchým obsahem textového obsahu elementu a ověřuje, zda je obsah aktuálního elementu dokončení u elementů se složitým obsahem.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Přeskočí ověření aktuálního obsahu elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt, který chcete ověřit obsah v kontextu nadřazeného elementu.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Ukončí ověření a ověří identitu omezení pro celý dokument XML, zda <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> nastavena možnost ověření.|  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaValidator> Třída má definované stavu přechodu, který vynucuje pořadí a výskytem volání do každé z metod popsaných v předchozí tabulce. Určitém stavu přechod <xref:System.Xml.Schema.XmlSchemaValidator> třída je popsaný v části "Přechod stavu XmlSchemaValidator" v tomto tématu.  
  
 Příklad metody použité k ověření prvky, atributy a obsah informační sadu XML podívejte se na příklad v předchozí části. Další informace o těchto metodách v tématu <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a>Ověření obsahu pomocí XmlValueGetter  
 <xref:System.Xml.Schema.XmlValueGetter> `delegate` Slouží k předat hodnotu atributu, text nebo prázdný uzly jako typy Common Language Runtime (CLR) kompatibilní s typem jazyk definice schématu XML (XSD) atribut, text nebo mezer uzlu. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Je užitečné, pokud hodnota CLR atribut, text nebo mezer uzel je již k dispozici a zabraňuje náklady na jeho převodu `string` a pak ho znovu reparsing pro ověření.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, A <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> metody jsou přetížené a přijměte hodnotu atributu, text nebo prázdný uzly jako `string` nebo <xref:System.Xml.Schema.XmlValueGetter> `delegate`.  
  
 Tyto metody <xref:System.Xml.Schema.XmlSchemaValidator> třída přijmout <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 Následuje příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate` převzaty z <xref:System.Xml.Schema.XmlSchemaValidator> příklad třídy v úvodu. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Vrátí hodnotu atributu jako <xref:System.DateTime> objektu. Chcete-li to ověřit <xref:System.DateTime> objekt vrácený <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> objekt nejprve převeden na typ hodnoty (ValueType je výchozí mapování CLR pro typ XSD) pro datový typ atributu, a pak omezující vlastnosti kontroly na převedenou hodnota.  
  
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
  
 Pro kompletní příklad, jak <xref:System.Xml.Schema.XmlValueGetter> `delegate`, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlValueGetter> `delegate`, najdete v článku <xref:System.Xml.Schema.XmlValueGetter>, a <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
#### <a name="post-schema-validation-information"></a>Po-Schema--informace o ověření  
 <xref:System.Xml.Schema.XmlSchemaInfo> Třída reprezentuje některé po-Schema-ověření-informace o uzlu XML ověřen <xref:System.Xml.Schema.XmlSchemaValidator> třídy. Různé metody <xref:System.Xml.Schema.XmlSchemaValidator> třída přijmout <xref:System.Xml.Schema.XmlSchemaInfo> objektu jako volitelný, (`null`) `out` parametr.  
  
 Po úspěšném ověření vlastnosti <xref:System.Xml.Schema.XmlSchemaInfo> objektu se nastavují s výsledky ověření. Například po úspěšné ověření použití atributu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> objektu je (Pokud je zadána) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> vlastnosti se nastavují s výsledky ověření .  
  
 Následující <xref:System.Xml.Schema.XmlSchemaValidator> přijmout metody třídy <xref:System.Xml.Schema.XmlSchemaInfo> objektu jako výstupní parametr.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 Pro kompletní příklad, jak <xref:System.Xml.Schema.XmlSchemaInfo> třídy, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaInfo> naleznete <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci k nástroji.  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Načítání očekávané částice, atributy a neurčené výchozí atributy  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody se načíst očekávaný částice, atributy a neurčené výchozí atributy v aktuálním kontextu ověřování.  
  
#### <a name="retrieving-expected-particles"></a>Načítání očekávané částice  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaParticle> objekty, které obsahují očekávané částice v aktuálním kontextu elementu. Platný částice, které mohou být vráceny <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jsou instancemi třídy <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAny> třídy.  
  
 Pokud je složku pro model obsahu `xs:sequence`, je vrácena pouze další částice v pořadí. Pokud je složku pro model obsahu `xs:all` nebo `xs:choice`, pak jsou vráceny všechny platné částice, které mohou být za v aktuálním kontextu elementu.  
  
> [!NOTE]
>  Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána hned po volání <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí všechny elementy globální.  
  
 Například v XML schéma Definition Language (XSD) schématu a XML dokumentu následujících, po ověření `book` elementu, `book` element je aktuální kontext elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `title` elementu. Pokud je kontext ověřování `title` elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí prázdné pole. Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `title` element byl ověřen ale předtím, než `description` element byl ověřen, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `description` element. Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `description` ověřila element pak vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaAny> objekt reprezentující zástupný znak.  
  
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
  
 V příkladu vezme jako vstupní následující kód XML.  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 V příkladu následující schéma XSD vezme jako vstupní.  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na aktuální kontext ověřován. Další informace najdete v části "Ověření kontextu" v tomto tématu.  
  
 Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
#### <a name="retrieving-expected-attributes"></a>Načítání očekávané atributů  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaAttribute> objekty, které obsahují očekávané atributy v aktuálním kontextu elementu.  
  
 V příkladu v úvodu, například <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda se používá k načtení všech atributů z `book` elementu.  
  
 Když zavoláte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda ihned po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metoda, jsou vráceny všechny atributy, které může zobrazit v dokumentu XML. Ale při volání <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda po jeden nebo více volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metoda, jsou vráceny atributy, které ještě nebyly byl ověřen pro aktuální element.  
  
> [!NOTE]
>  Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na aktuální kontext ověřován. Další informace najdete v části "Ověření kontextu" v tomto tématu.  
  
 Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda, podívejte se na příklad v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
#### <a name="retrieving-unspecified-default-attributes"></a>Načítání neurčené výchozí atributy  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda naplní <xref:System.Collections.ArrayList> zadaným <xref:System.Xml.Schema.XmlSchemaAttribute> objekty pro atributy s výchozími hodnotami, které nebyly ověřeny dříve pomocí <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metoda v kontextu elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla být volána po volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metodu na jednotlivé atributy v kontextu elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda slouží k určení, co má být vložen do dokumentu XML během ověřování jsou výchozí atributy.  
  
 Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.  
  
### <a name="handling-schema-validation-events"></a>Zpracování událostí ověření schématu  
 Schéma ověřování upozornění a chyb zjištěných při ověřování jsou zpracovávány <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> události <xref:System.Xml.Schema.XmlSchemaValidator> třídy.  
  
 Upozornění na ověření schématu mít <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>. Pokud žádné <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> byl přiřazen, <xref:System.Xml.Schema.XmlSchemaValidationException> je vyvolána pro všechny chyby ověřování schématu s <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>. Však <xref:System.Xml.Schema.XmlSchemaValidationException> není pro schéma ověřování upozornění s vyvolána <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning>.  
  
 Tady je příklad <xref:System.Xml.Schema.ValidationEventHandler> která přijme, schématu ověření upozornění a chyb zjištěných při ověřování schématu prováděné z příkladu v úvodu.  
  
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
  
 Pro kompletní příklad, jak <xref:System.Xml.Schema.ValidationEventHandler>, podívejte se na příklad v úvodu. Další informace najdete v tématu <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci k nástroji.  
  
## <a name="xmlschemavalidator-state-transition"></a>Přechod stavu XmlSchemaValidator  
 <xref:System.Xml.Schema.XmlSchemaValidator> Třída má definované stavu přechodu, který vynucuje pořadí a výskytem volání do každé metody použité k ověření prvky, atributy a obsah informační sadu XML.  
  
 Následující tabulka popisuje přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třída a pořadí a výskytem volání metod, které lze provést v každém stavu.  
  
|Stav|Přechod|  
|-----------|----------------|  
|Ověření|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>(<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel*)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|  
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|  
|Prvek|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;|  
|Obsah|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|  
  
> [!NOTE]
>  <xref:System.InvalidOperationException> Je vyvolána každou z metod v tabulce výše při volání metody je v nesprávné pořadí podle aktuálního stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.  
  
 Výše uvedené tabulce přechod stavu pomocí interpunkčních znamének popisují metody a dalších stavy, které lze volat pro každý stav přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy. Symboly použité jsou stejné symboly nalézt v odkazu standardy XML pro dokument typu definice (DTD).  
  
 Následující tabulka popisuje vliv metody interpunkčních znamének najít v předchozí tabulce přechod stavu a dalších stavy, které lze volat pro každý stav v přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.  
  
|Symbol|Popis|  
|------------|-----------------|  
|&#124;|Je možné volat metody nebo stavu (jeden před panelu) nebo jedna za ním.|  
|?|Metoda nebo stavu, který předchází otazník je volitelný, ale pokud je volána ho lze volat pouze jednou.|  
|*|Metoda nebo stavu, který předchází * symbol je volitelná a lze volat více než jednou.|  
  
## <a name="validation-context"></a>Kontext ověřování  
 Metody <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření prvky, atributy a obsah informační sadu XML, změňte ověření kontextu <xref:System.Xml.Schema.XmlSchemaValidator> objektu. Například <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> metoda přeskočí ověření aktuálního obsahu elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objektu ověřování obsahu v kontextu nadřazeného elementu; je ekvivalentní k přeskočení ověření pro všechny podřízené objekty aktuálního elementu a pak volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metoda.  
  
 Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na aktuální kontext ověřován.  
  
 Následující tabulka popisuje výsledky volání těchto metod po volání jedné z metod <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření prvky, atributy a obsah informační sadu XML.  
  
|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pole obsahující všechny globální elementy.<br /><br /> Pokud přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, která přijímá <xref:System.Xml.Schema.XmlSchemaObject> k chybě při inicializaci částečné ověřování elementu, se nazývá parametr <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.|Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> Pokud přetížení <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, která použije <xref:System.Xml.Schema.XmlSchemaObject> k chybě při inicializaci částečné ověřování atributu, se nazývá parametr <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut, na kterou <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.|Přidá schéma tak, aby <xref:System.Xml.Schema.XmlSchemaSet> z <xref:System.Xml.Schema.XmlSchemaValidator> objektu, pokud má žádné předběžného zpracování chyby.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Pokud element kontextu je platný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů očekáván jako podřízené objekty daného elementu kontextu.<br /><br /> Pokud element kontextu je neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.|Pokud element kontextu je platný a pokud bez volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> byl dříve proveden, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam hodnot všechny atributy, které jsou definované v kontextu elementu.<br /><br /> Pokud již byly ověřeny některé atributy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam hodnot zbývající atributy, které má být ověřen.<br /><br /> Pokud element kontextu je neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Pokud je atribut kontext atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů očekávání jako první podřízený element kontextu.|Pokud je atribut kontext atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývající atributů má být ověřen.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Vrátí pořadí elementů očekávání jako první podřízený element kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí seznam hodnot požadované a volitelné atributy, které ještě mají být ověřen pro element kontextu.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Vrátí pořadí elementů očekávání jako první podřízený element kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>vrátí prázdné pole.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Pokud je Přimíchán element kontextu contentType, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů v další pozice se očekává.<br /><br /> Pokud je element kontextu contentType typu TextOnly nebo je prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> Pokud je element kontextu contentType ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů v další pozice ale chybu ověření byl očekáván již došlo.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí element kontextu seznam atributů nebyl ověřen.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Pokud mezer kontextu je nejvyšší úrovně mezer <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Pokud mezer kontextu je nejvyšší úrovně mezer <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Vrátí pořadí elementů byl očekáván po elementu kontextu (možné na stejné úrovni).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí element kontextu seznam atributů nebyl ověřen.<br /><br /> Pokud element kontextu nemá nadřazený pak <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrací prázdný seznam (element kontextu je nadřazená aktuálního elementu, na kterém <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> byla volána).|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako výše.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Vrátí prázdné pole.|Vrátí prázdné pole.|Stejné jako výše.|  
  
> [!NOTE]
>  Hodnot vrácených různé vlastnosti <xref:System.Xml.Schema.XmlSchemaValidator> třídy nejsou změněna voláním některou z metod v předchozí tabulce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Schema.XmlSchemaValidator>
