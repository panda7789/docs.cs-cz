---
title: XmlSchemaValidator ověřování založené na nabízených oznámeních
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a420a134eda6c62758b0d218e3c0a4a4922b048c
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250045"
---
# <a name="xmlschemavalidator-push-based-validation"></a>XmlSchemaValidator ověřování založené na nabízených oznámeních

Třída <xref:System.Xml.Schema.XmlSchemaValidator> poskytuje účinný a vysoce výkonný mechanismus pro ověřování XML dat proti schématům XML ve způsobu založeném na nabízených oznámeních. Například třída <xref:System.Xml.Schema.XmlSchemaValidator> umožňuje ověřit místně XML informační sadu bez nutnosti jejich serializace jako dokument XML a pak znovu analyzovat dokument pomocí ověřování XML Reader.

Třída <xref:System.Xml.Schema.XmlSchemaValidator> se dá použít v pokročilých scénářích, jako je vytváření ověřovacích modulů pro vlastní zdroje dat XML, nebo jako způsob, jak vytvořit ověřovací zapisovač XML.

Následuje příklad použití třídy <xref:System.Xml.Schema.XmlSchemaValidator> k ověření souboru `contosoBooks.xml` proti schématu `contosoBooks.xsd`. V příkladu se používá třída <xref:System.Xml.Serialization.XmlSerializer> k deserializaci souboru `contosoBooks.xml` a předání hodnoty uzlů do metod třídy <xref:System.Xml.Schema.XmlSchemaValidator>.

> [!NOTE]
> Tento příklad se používá v celém oddílu tohoto tématu.

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

V příkladu se jako vstup používá soubor `contosoBooks.xml`.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Příklad také přebírá `contosoBooks.xsd` jako vstup.

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

Chcete-li zahájit ověřování XML informační sady, je nutné nejprve inicializovat novou instanci třídy <xref:System.Xml.Schema.XmlSchemaValidator> pomocí konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>.

Konstruktor <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> přebírá objekty <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet> a <xref:System.Xml.XmlNamespaceManager> jako parametry a jako parametr hodnotu <xref:System.Xml.Schema.XmlSchemaValidationFlags>. Objekt <xref:System.Xml.XmlNameTable> se používá k atomizovatí známých řetězců oboru názvů, jako je například obor názvů schématu, obor názvů XML a tak dále, a je předán metodě <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> při ověřování jednoduchého obsahu. Objekt <xref:System.Xml.Schema.XmlSchemaSet> obsahuje schémata XML sloužící k ověření XML informační sady. Objekt <xref:System.Xml.XmlNamespaceManager> se používá k překladu oborů názvů zjištěných během ověřování. Hodnota <xref:System.Xml.Schema.XmlSchemaValidationFlags> slouží k zakázání určitých funkcí ověřování.

Další informace o konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="initializing-validation"></a>Inicializuje se ověřování.

Po sestavení objektu <xref:System.Xml.Schema.XmlSchemaValidator> existují dvě přetížené metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, které se používají k inicializaci stavu objektu <xref:System.Xml.Schema.XmlSchemaValidator>. Níže jsou uvedené dvě metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

Výchozí metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicializuje objekt <xref:System.Xml.Schema.XmlSchemaValidator> do svého počátečního stavu a metoda přetížení <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, která převezme <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, inicializuje objekt <xref:System.Xml.Schema.XmlSchemaValidator> do počátečního stavu pro částečné ověření.

Metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> lze volat pouze ihned po vytvoření objektu <xref:System.Xml.Schema.XmlSchemaValidator> nebo po volání <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.

Příklad metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> naleznete v příkladu v úvodu. Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="partial-validation"></a>Částečné ověření

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje objekt <xref:System.Xml.Schema.XmlSchemaValidator> do svého počátečního stavu pro částečné ověření.

V následujícím příkladu je <xref:System.Xml.Schema.XmlSchemaObject> inicializován pro částečné ověřování pomocí metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>. Prvek schématu `orderNumber` se předává výběrem elementu schématu <xref:System.Xml.XmlQualifiedName> v kolekci <xref:System.Xml.Schema.XmlSchemaObjectTable>, kterou vrátí vlastnost <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> objektu <xref:System.Xml.Schema.XmlSchemaSet>. Objekt <xref:System.Xml.Schema.XmlSchemaValidator> poté ověří tento konkrétní element.

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

Příklad má jako vstup následující schéma XML.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="adding-additional-schemas"></a>Přidání dalších schémat

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> slouží k přidání schématu XML do sady schémat používaných při ověřování. Metodu <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> lze použít k simulaci efektu zaznamenání vloženého schématu XML v ověřované XML informační službě.

> [!NOTE]
> Cílový obor názvů parametru <xref:System.Xml.Schema.XmlSchema> se nemůže shodovat s žádným prvkem nebo atributem, který objekt <xref:System.Xml.Schema.XmlSchemaValidator> již zjistil.
>
> Pokud hodnota <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> nebyla předána jako parametr konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> neprovede žádnou akci.

Výsledek metody <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> závisí na ověřování aktuálního kontextu uzlu XML. Další informace o kontextech ověřování naleznete v části "kontext ověření" v tomto tématu.

Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="validating-elements-attributes-and-content"></a>Ověřování elementů, atributů a obsahu

Třída <xref:System.Xml.Schema.XmlSchemaValidator> poskytuje několik metod, které slouží k ověření elementů, atributů a obsahu v XML informačním souboru pro schémata XML. Následující tabulka popisuje každou z těchto metod.

|Metoda|Description|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Ověří název elementu v aktuálním kontextu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Ověří atribut v kontextu aktuálního prvku nebo s objektem <xref:System.Xml.Schema.XmlSchemaAttribute> předaným jako parametr metodě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Ověřuje, zda jsou přítomny všechny požadované atributy v kontextu elementu, a připraví objekt <xref:System.Xml.Schema.XmlSchemaValidator> k ověření podřízeného obsahu elementu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Ověří, zda je povolen text v kontextu aktuálního prvku, a nashromáždí text pro ověření, pokud má aktuální prvek jednoduchý obsah.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Ověří, zda je v aktuálním kontextu prvku povoleno prázdné místo a zda má aktuální prvek jednoduchý obsah, a nashromáždí prázdný prostor pro ověřování.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Ověřuje, zda je textový obsah elementu platný vzhledem k jeho datovému typu pro prvky s jednoduchým obsahem a ověřuje, zda je obsah aktuálního prvku dokončen pro prvky se složitým obsahem.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Přeskočí ověřování aktuálního obsahu elementu a připraví objekt <xref:System.Xml.Schema.XmlSchemaValidator> pro ověření obsahu v kontextu nadřazeného elementu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Ukončí ověřování a zkontroluje omezení identity pro celý dokument XML, pokud je nastavena možnost ověřování <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints>.|

> [!NOTE]
> Třída <xref:System.Xml.Schema.XmlSchemaValidator> má definovaný přechod stavu, který vynutila sekvenci a výskyt volání jednotlivých metod popsaných v předchozí tabulce. Konkrétní přechod stavu třídy <xref:System.Xml.Schema.XmlSchemaValidator> je popsán v tomto tématu v části "přechod stavu XmlSchemaValidator".

Příklad metod, které slouží k ověření elementů, atributů a obsahu v informační příručce XML, naleznete v příkladu v předchozí části. Další informace o těchto metodách naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>Ověřování obsahu pomocí XmlValueGetter

@No__t-0 @ no__t-1 lze použít k předání hodnoty atributu, textu nebo prázdných uzlů jako typů modulu CLR (Common Language Runtime), které jsou kompatibilní s typem jazyka XML Schema Definition Language (XSD) atributu, textu nebo bílého prostoru. @No__t-0 @ no__t-1 je užitečné, pokud je hodnota CLR v uzlu atributu, textu nebo prázdného prostoru již k dispozici, a vyhněte se nákladům na jejich převod na `string` a opětovnou analýzou pro ověření.

Metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> a <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> jsou přetížené a přijímají hodnotu atributu, textu nebo prázdných uzlů jako `string` nebo <xref:System.Xml.Schema.XmlValueGetter> @ no__t-5.

Následující metody třídy <xref:System.Xml.Schema.XmlSchemaValidator> přijímají jako parametr <xref:System.Xml.Schema.XmlValueGetter> @ no__t-2.

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

Níže je uveden příklad <xref:System.Xml.Schema.XmlValueGetter> @ no__t-1 pořízených z příkladu třídy <xref:System.Xml.Schema.XmlSchemaValidator> v úvodu. @No__t-0 @ no__t-1 vrátí hodnotu atributu jako objekt <xref:System.DateTime>. Chcete-li ověřit, zda objekt <xref:System.DateTime> vrácený <xref:System.Xml.Schema.XmlValueGetter>, objekt <xref:System.Xml.Schema.XmlSchemaValidator> nejprve převede na typ ValueType (ValueType je výchozí mapování CLR pro typ XSD) pro datový typ atributu a poté zkontroluje charakteristiky převedené hodnoty.

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

Úplný příklad <xref:System.Xml.Schema.XmlValueGetter> @ no__t-1 naleznete v příkladu v úvodu. Další informace o <xref:System.Xml.Schema.XmlValueGetter> @ no__t-1 naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlValueGetter> a <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="post-schema-validation-information"></a>Po ověření schématu – informace

Třída <xref:System.Xml.Schema.XmlSchemaInfo> představuje některé z informací o ověřování po schématu, které jsou ověřeny třídou <xref:System.Xml.Schema.XmlSchemaValidator>. Různé metody třídy <xref:System.Xml.Schema.XmlSchemaValidator> přijímají objekt <xref:System.Xml.Schema.XmlSchemaInfo> jako volitelný parametr (`null`) `out`.

Po úspěšném ověření jsou vlastnosti objektu <xref:System.Xml.Schema.XmlSchemaInfo> nastaveny s výsledky ověření. Například po úspěšném ověření atributu pomocí metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> jsou vlastnosti objektu <xref:System.Xml.Schema.XmlSchemaInfo> (je-li zadán) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> nastaveny s výsledky ověření.

Následující metody třídy <xref:System.Xml.Schema.XmlSchemaValidator> přijímají objekt <xref:System.Xml.Schema.XmlSchemaInfo> jako výstupní parametr.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

Úplný příklad třídy <xref:System.Xml.Schema.XmlSchemaInfo> naleznete v příkladu v úvodu. Další informace o třídě <xref:System.Xml.Schema.XmlSchemaInfo> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaInfo>.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Načítání očekávaných částic, atributů a nespecifikovaných výchozích atributů

Třída <xref:System.Xml.Schema.XmlSchemaValidator> poskytuje metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> k načtení očekávaných částic, atributů a nespecifikovaných výchozích atributů v aktuálním kontextu ověřování.

#### <a name="retrieving-expected-particles"></a>Načítání očekávaných částic

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací pole objektů <xref:System.Xml.Schema.XmlSchemaParticle>, které obsahují očekávané částice v kontextu aktuálního prvku. Platné částice, které mohou být vráceny metodou <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, jsou instance <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAny> třídy.

Když je obsah modelu obsahu `xs:sequence`, vrátí se pouze další částice v sekvenci. Pokud je kompozice pro model obsahu `xs:all` nebo `xs:choice`, budou vráceny všechny platné částice, které by mohly následovat v kontextu aktuálního prvku.

> [!NOTE]
> Pokud je metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> volána bezprostředně po volání metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, vrátí metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> všechny globální prvky.

Například v schématu XML Schema Definition Language (XSD) a dokumentu XML, který následuje, po ověření elementu `book` je prvek `book` aktuálním kontextem elementu. Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací pole obsahující jeden objekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentující prvek `title`. Když je kontext ověření prvkem `title`, metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole. Je-li metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> volána po ověření prvku `title`, ale před ověřením elementu `description`, vrátí pole obsahující jeden objekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentující `description` element. Pokud je volána metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> po ověření prvku `description`, vrátí pole obsahující jeden objekt <xref:System.Xml.Schema.XmlSchemaAny> reprezentující zástupný znak.

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
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

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
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

 Příklad má jako vstup následující kód XML:

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

Příklad má jako vstup následující schéma XSD:

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> Výsledky metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> jsou závislé na ověřeném aktuálním kontextu. Další informace najdete v části "kontext ověření" v tomto tématu.

Příklad metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> naleznete v příkladu v úvodu. Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="retrieving-expected-attributes"></a>Načítání očekávaných atributů

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrací pole objektů <xref:System.Xml.Schema.XmlSchemaAttribute>, které obsahují očekávané atributy v kontextu aktuálního prvku.

Například v příkladu v úvodu se metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> používá k načtení všech atributů prvku `book`.

Pokud zavoláte metodu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> hned za metodou <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>, vrátí se všechny atributy, které by mohly být zobrazeny v dokumentu XML. Nicméně pokud zavoláte metodu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> po jednom nebo více volání metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, vrátí se atributy, které ještě nebyly ověřeny pro aktuální prvek.

> [!NOTE]
> Výsledky metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> jsou závislé na ověřeném aktuálním kontextu. Další informace najdete v části "kontext ověření" v tomto tématu.

Příklad metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> naleznete v příkladu v úvodu. Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="retrieving-unspecified-default-attributes"></a>Načítání nespecifikovaných výchozích atributů

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> naplní <xref:System.Collections.ArrayList> zadané objekty <xref:System.Xml.Schema.XmlSchemaAttribute> pro všechny atributy s výchozími hodnotami, které nebyly dříve ověřeny pomocí metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> v kontextu elementu. Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> by měla být volána po volání metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> u každého atributu v kontextu elementu. Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> by měla být použita k určení, které výchozí atributy budou vloženy do ověřovaného dokumentu XML.

Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="handling-schema-validation-events"></a>Zpracování událostí ověřování schématu

Upozornění a chyby ověřování schématu zjištěné při ověřování jsou zpracovávány událostí <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> třídy <xref:System.Xml.Schema.XmlSchemaValidator>.

Upozornění ověřování schématu mají hodnotu <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu mají hodnotu <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error>. Pokud nebyla přiřazena žádná <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler>, je vyvolána <xref:System.Xml.Schema.XmlSchemaValidationException> pro všechny chyby ověřování schématu s hodnotou <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error>. @No__t-0 však není vyvolána pro upozornění ověřování schématu s hodnotou <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Warning>.

Následuje příklad <xref:System.Xml.Schema.ValidationEventHandler>, který přijímá upozornění ověřování schématu a chyby zjištěné v průběhu ověřování schématu provedeného v příkladu v úvodu.

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

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

Úplný příklad <xref:System.Xml.Schema.ValidationEventHandler> naleznete v příkladu v úvodu. Další informace naleznete v referenční dokumentaci ke třídě <xref:System.Xml.Schema.XmlSchemaInfo>.

## <a name="xmlschemavalidator-state-transition"></a>Přechod stavu XmlSchemaValidator

Třída <xref:System.Xml.Schema.XmlSchemaValidator> má definovaný přechod stavu, který vynutila sekvenci a výskyt volání v každé z metod používaných k ověřování elementů, atributů a obsahu v XML XML.

Následující tabulka popisuje přechod stavu třídy <xref:System.Xml.Schema.XmlSchemaValidator> a sekvence a výskyt volání metody, které lze provést v každém stavu.

|Stav|Přejít|
|-----------|----------------|
|Oproti|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; Toplevel *) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|Element @no__t- &#124; 0 @no__t- &#124; 2|
|Prvek|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> * (obsah <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> @ no__t-3)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> @ no__t-2 <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> @ no__t-2 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> obsah @ no__t-4 <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;|
|Obsah|Element @no__t- &#124; 0 @no__t- &#124; 2|

> [!NOTE]
> @No__t-0 je vyvolána každou metodou v tabulce výše, pokud je volání metody provedeno v nesprávné sekvenci podle aktuálního stavu objektu <xref:System.Xml.Schema.XmlSchemaValidator>.

Výše uvedená tabulka přechodu stavu používá interpunkční znaménka k popisu metod a dalších stavů, které lze volat pro každý stav přechodu stavu třídy <xref:System.Xml.Schema.XmlSchemaValidator>. Použité symboly jsou stejné symboly, které najdete v referenčních standardech XML pro definici typu dokumentu (DTD).

Následující tabulka popisuje, jak se symboly interpunkčních znamének v tabulce přechodu stavu nacházejí výše ovlivňují metody a další stavy, které mohou být volány pro každý stav v přechodu stavu třídy <xref:System.Xml.Schema.XmlSchemaValidator>.

|Symbol|Description|
|------------|-----------------|
|&#124;|Lze zavolat buď metodu, nebo stav (jeden před pruhový nebo ten).|
|?|Metoda nebo stav, který předchází otazník je volitelný, ale pokud je volána, lze ji volat pouze jednou.|
|*|Metoda nebo stav, který předchází symbolu * je volitelná a může být volána více než jednou.|

## <a name="validation-context"></a>Kontext ověřování

Metody třídy <xref:System.Xml.Schema.XmlSchemaValidator> používané k ověřování elementů, atributů a obsahu v XML informačním souboru, mění kontext ověření objektu <xref:System.Xml.Schema.XmlSchemaValidator>. Například metoda <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> přeskočí ověřování aktuálního obsahu elementu a připraví objekt <xref:System.Xml.Schema.XmlSchemaValidator> pro ověření obsahu v kontextu nadřazeného elementu; je ekvivalentní k přeskočení ověřování pro všechny podřízené položky aktuálního prvku a následnému volání metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.

Výsledky metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> jsou závislé na ověřeném aktuálním kontextu.

Následující tabulka popisuje výsledky volání těchto metod po volání jedné z metod třídy <xref:System.Xml.Schema.XmlSchemaValidator> používané k ověřování elementů, atributů a obsahu v XML informačním souboru.

|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Pokud je zavolána výchozí metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, vrátí <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> pole obsahující všechny globální prvky.<br /><br /> Pokud je volána přetížená metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr pro inicializaci částečného ověření prvku, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému byl inicializován objekt <xref:System.Xml.Schema.XmlSchemaValidator>.|Pokud je zavolána výchozí metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, vrátí <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> prázdné pole.<br /><br /> Pokud je volání metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametru pro inicializaci částečného ověřování atributu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut, na který byl inicializován objekt <xref:System.Xml.Schema.XmlSchemaValidator>.|Přidá schéma do <xref:System.Xml.Schema.XmlSchemaSet> objektu <xref:System.Xml.Schema.XmlSchemaValidator>, pokud nemá žádné chyby předzpracování.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Je-li prvek kontextu platný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávaných jako podřízené objekty kontextu elementu.<br /><br /> Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.|Pokud kontextový prvek je platný a pokud žádné volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> nebylo dříve provedeno, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam všech atributů definovaných v prvku Context.<br /><br /> Pokud některé atributy již byly ověřeny, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývajících atributů, které mají být ověřeny.<br /><br /> Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávanou jako první podřízený prvek kontextu.|Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> Jinak <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývajících atributů, které mají být ověřeny.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam požadovaných a volitelných atributů, které se ještě ověřují pro prvek kontextu.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Pokud je třída contentType elementu kontextu smíšená, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávanou na další pozici.<br /><br /> Pokud je třída contentType elementu kontextu typu TextOnly nebo prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> Pokud je objekt contentType elementu kontextu ElementOnly, vrátí <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sekvenci prvků očekávanou na další pozici, ale k chybě ověřování již došlo.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam atributů kontextového elementu, které nejsou ověřeny.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Pokud je v tomto kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V opačném případě je chování metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Pokud je v tomto kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> V opačném případě je chování metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací sekvenci prvků očekávaných po elementu Context (možné na stejné úrovni).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam atributů kontextového elementu, které nejsou ověřeny.<br /><br /> Pokud kontextový prvek nemá žádné nadřazené, potom <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdný seznam (kontextový prvek je nadřazeným prvkem aktuálního prvku, na kterém byla volána <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>).|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Vrátí prázdné pole.|Vrátí prázdné pole.|Stejné jako výše.|

> [!NOTE]
> Hodnoty vrácené různými vlastnostmi třídy <xref:System.Xml.Schema.XmlSchemaValidator> nejsou změněny voláním libovolné metody ve výše uvedené tabulce.

## <a name="see-also"></a>Související témata

- <xref:System.Xml.Schema.XmlSchemaValidator>
