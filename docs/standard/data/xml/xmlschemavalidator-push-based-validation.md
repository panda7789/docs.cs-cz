---
title: Přímé ověření XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: 6a0cc110c2b8bcd97b9f5c16a344db5a63046353
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709800"
---
# <a name="xmlschemavalidator-push-based-validation"></a>Přímé ověření XmlSchemaValidator

<xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje účinný a vysoce výkonný mechanismus pro ověřování dat XML proti schématům XML ve způsobu založeném na nabízených oznámeních. Například <xref:System.Xml.Schema.XmlSchemaValidator> třída umožňuje ověřit místně XML informační sadu bez nutnosti jejich serializace jako dokument XML a pak znovu analyzovat dokument s použitím ověřování XML Reader.

<xref:System.Xml.Schema.XmlSchemaValidator> Třída se dá použít v pokročilých scénářích, jako je vytváření ověřovacích modulů přes vlastní zdroje dat XML, nebo jako způsob, jak vytvořit ověřovací zapisovač XML.

Následuje příklad použití <xref:System.Xml.Schema.XmlSchemaValidator> třídy k ověření `contosoBooks.xml` souboru proti `contosoBooks.xsd` schématu. V příkladu se používá <xref:System.Xml.Serialization.XmlSerializer> třída k deserializaci `contosoBooks.xml` souboru a předání hodnoty uzlů do metod <xref:System.Xml.Schema.XmlSchemaValidator> třídy.

> [!NOTE]
> Tento příklad se používá v celém oddílu tohoto tématu.

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

Příklad přebírá `contosoBooks.xml` soubor jako vstup.

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

Chcete-li zahájit ověřování XML informační sady, je nutné nejprve inicializovat novou instanci <xref:System.Xml.Schema.XmlSchemaValidator> třídy pomocí <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru.

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Konstruktor přebírá <xref:System.Xml.XmlNameTable>objekty <xref:System.Xml.Schema.XmlSchemaSet>, a <xref:System.Xml.XmlNamespaceManager> jako parametry a jako <xref:System.Xml.Schema.XmlSchemaValidationFlags> hodnotu jako parametr. <xref:System.Xml.XmlNameTable> Objekt se používá k atomizovat dobře známých řetězců oboru názvů, jako je například obor názvů schématu, obor názvů XML a tak dále, a je předán <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metodě při ověřování jednoduchého obsahu. <xref:System.Xml.Schema.XmlSchemaSet> Objekt obsahuje schémata XML sloužící k ověření XML informační sady. <xref:System.Xml.XmlNamespaceManager> Objekt se používá k překladu oborů názvů zjištěných během ověřování. <xref:System.Xml.Schema.XmlSchemaValidationFlags> Hodnota se používá k zakázání určitých funkcí ověřování.

Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci třídy.

### <a name="initializing-validation"></a>Inicializuje se ověřování.

Po sestavení <xref:System.Xml.Schema.XmlSchemaValidator> objektu jsou k dispozici dvě přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, které se používají k inicializaci stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu. Níže jsou uvedené dvě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Výchozí metoda inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt do svého počátečního stavu a přetíženou <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metodu, která přijímá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt do svého počátečního stavu pro částečné ověření.

Obě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody lze volat pouze ihned po sestavení <xref:System.Xml.Schema.XmlSchemaValidator> objektu nebo po volání. <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>

Příklad <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody naleznete v příkladu v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodě naleznete v referenční dokumentaci ke <xref:System.Xml.Schema.XmlSchemaValidator> třídě.

#### <a name="partial-validation"></a>Částečné ověření

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metoda, která přijímá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt do svého počátečního stavu pro částečné ověření.

V následujícím příkladu <xref:System.Xml.Schema.XmlSchemaObject> je inicializováno pro částečné ověřování pomocí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody. Prvek `orderNumber` schématu je předán výběrem elementu <xref:System.Xml.XmlQualifiedName> schématu v <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekci vrácené <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> vlastností <xref:System.Xml.Schema.XmlSchemaSet> objektu. <xref:System.Xml.Schema.XmlSchemaValidator> Objekt potom ověří tento konkrétní element.

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

Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodě naleznete v referenční dokumentaci ke <xref:System.Xml.Schema.XmlSchemaValidator> třídě.

### <a name="adding-additional-schemas"></a>Přidání dalších schémat

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda <xref:System.Xml.Schema.XmlSchemaValidator> třídy slouží k přidání schématu XML do sady schémat používaných při ověřování. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda může být použita k simulaci efektu zaznamenání vloženého schématu XML do ověřované XML informační sady.

> [!NOTE]
> Cílový obor názvů <xref:System.Xml.Schema.XmlSchema> parametru nemůže odpovídat žádnému elementu nebo atributu, který je <xref:System.Xml.Schema.XmlSchemaValidator> již v objektu nalezen.
>
> Pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> hodnota nebyla předána jako parametr <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda neprovede žádnou akci.

Výsledek <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody závisí na ověření aktuálního kontextu uzlu XML. Další informace o kontextech ověřování naleznete v části "kontext ověření" v tomto tématu.

Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metodě naleznete v referenční dokumentaci ke <xref:System.Xml.Schema.XmlSchemaValidator> třídě.

### <a name="validating-elements-attributes-and-content"></a>Ověřování elementů, atributů a obsahu

<xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje několik metod, které slouží k ověření elementů, atributů a obsahu v XML informačním souboru pro schémata XML. Následující tabulka popisuje každou z těchto metod.

|Metoda|Popis|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Ověří název elementu v aktuálním kontextu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Ověří atribut v kontextu aktuálního prvku nebo <xref:System.Xml.Schema.XmlSchemaAttribute> objektu předaného jako parametr <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodě.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Ověřuje, zda jsou přítomny všechny požadované atributy v kontextu elementu, a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt k ověření podřízeného obsahu elementu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Ověří, zda je povolen text v kontextu aktuálního prvku, a nashromáždí text pro ověření, pokud má aktuální prvek jednoduchý obsah.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Ověří, zda je v aktuálním kontextu prvku povoleno prázdné místo a zda má aktuální prvek jednoduchý obsah, a nashromáždí prázdný prostor pro ověřování.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Ověřuje, zda je textový obsah elementu platný vzhledem k jeho datovému typu pro prvky s jednoduchým obsahem a ověřuje, zda je obsah aktuálního prvku dokončen pro prvky se složitým obsahem.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Přeskočí ověřování aktuálního obsahu elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt k ověření obsahu v kontextu nadřazeného elementu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Ukončí ověřování a zkontroluje omezení identity pro celý dokument XML, pokud je <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> nastavena možnost ověřování.|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator> Třída má definovaný přechod stavu, který vynutila sekvenci a výskyt volání každé z metod popsaných v předchozí tabulce. Konkrétní přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy je popsán v tomto tématu v části "přechod stavu XmlSchemaValidator".

Příklad metod, které slouží k ověření elementů, atributů a obsahu v informační příručce XML, naleznete v příkladu v předchozí části. Další informace o těchto metodách naleznete v referenční <xref:System.Xml.Schema.XmlSchemaValidator> dokumentaci ke třídě.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>Ověřování obsahu pomocí XmlValueGetter

<xref:System.Xml.Schema.XmlValueGetter> Lze použít k předání hodnoty atributu, textu nebo prázdných uzlů jako typů modulu CLR (Common Language Runtime), které jsou kompatibilní s typem jazyka XML Schema Definition Language (XSD) atributu, textu nebo prázdného `delegate` uzlu. Je užitečné, pokud je hodnota CLR uzlu, textu nebo prázdného prostoru již k dispozici, a nepoužívejte náklady na jejich převod na `string` a pak znovu znovu analyzovat pro ověření. <xref:System.Xml.Schema.XmlValueGetter> `delegate`

Metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>a <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> jsou přetížené a přijímají hodnotu atributu, textu nebo prázdných uzlů jako `string` nebo. <xref:System.Xml.Schema.XmlValueGetter> `delegate`

Následující metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy přijímají <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

Následuje příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate` , který je povedený <xref:System.Xml.Schema.XmlSchemaValidator> z příkladu třídy v úvodu. Vrátí hodnotu atributu jako <xref:System.DateTime> objekt. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Chcete-li <xref:System.DateTime> ověřit <xref:System.Xml.Schema.XmlValueGetter>, že <xref:System.Xml.Schema.XmlSchemaValidator> objekt vrácený, objekt nejprve převede na ValueType (ValueType je výchozí mapování CLR pro typ XSD) pro datový typ atributu a poté zkontroluje charakteristiky převedené hodnoty.

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

Úplný příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate`naleznete v příkladu v úvodu. Další <xref:System.Xml.Schema.XmlValueGetter> `delegate`informace o <xref:System.Xml.Schema.XmlValueGetter>naleznete v dokumentaci ke třídě a <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci k ní.

#### <a name="post-schema-validation-information"></a>Po ověření schématu – informace

<xref:System.Xml.Schema.XmlSchemaInfo> Třída reprezentuje některé z informací o ověřování po schématu, které jsou v uzlu XML ověřené <xref:System.Xml.Schema.XmlSchemaValidator> třídou. Různé metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy přijímají <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako volitelný parametr, (`null`). `out`

Po úspěšném ověření jsou vlastnosti <xref:System.Xml.Schema.XmlSchemaInfo> objektu nastaveny s výsledky ověření. Například <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> po úspěšném ověření atributu pomocí metody je <xref:System.Xml.Schema.XmlSchemaInfo> objekt (je-li zadán) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> vlastností nastaven s výsledky ověření.

Následující <xref:System.Xml.Schema.XmlSchemaValidator> metody třídy přijímají <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako výstupní parametr.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

Úplný příklad této <xref:System.Xml.Schema.XmlSchemaInfo> třídy naleznete v příkladu v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaInfo> třídě naleznete v <xref:System.Xml.Schema.XmlSchemaInfo> referenční dokumentaci třídy.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Načítání očekávaných částic, atributů a nespecifikovaných výchozích atributů

<xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> pro načtení očekávaných částic, atributů a nespecifikovaných výchozích atributů v aktuálním kontextu ověřování.

#### <a name="retrieving-expected-particles"></a>Načítání očekávaných částic

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrací pole <xref:System.Xml.Schema.XmlSchemaParticle> objektů, které obsahují očekávané částice v kontextu aktuálního prvku. Platné částice, které mohou být vráceny <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodou, jsou instance třídy <xref:System.Xml.Schema.XmlSchemaElement> a. <xref:System.Xml.Schema.XmlSchemaAny>

Když je kompozice modelu obsahu `xs:sequence`, vrátí se pouze další částice v sekvenci. Pokud je kompozice modelu obsahu `xs:all` nebo a `xs:choice`, pak jsou vráceny všechny platné částice, které by mohly následovat v kontextu aktuálního prvku.

> [!NOTE]
> Pokud je <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda volána bezprostředně po volání <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí všechny globální prvky.

Například v schématu XML schématu (XSD) a dokumentu XML, který následuje, je po ověření `book` elementu `book` element prvkem aktuální kontext prvku. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `title` element. Když je kontext ověření `title` element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí prázdné pole. Pokud je <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> `title` metoda volána po ověření prvku, ale před ověřením `description` elementu, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `description` prvek. Pokud je <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda volána po ověření `description` elementu, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaAny> objekt reprezentující zástupný znak.

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
> Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metod <xref:System.Xml.Schema.XmlSchemaValidator> , <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>a třídy jsou závislé na ověřeném aktuálním kontextu. Další informace najdete v části "kontext ověření" v tomto tématu.

Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody naleznete v příkladu v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodě naleznete v referenční dokumentaci ke <xref:System.Xml.Schema.XmlSchemaValidator> třídě.

#### <a name="retrieving-expected-attributes"></a>Načítání očekávaných atributů

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda vrací pole <xref:System.Xml.Schema.XmlSchemaAttribute> objektů, které obsahují očekávané atributy v kontextu aktuálního prvku.

Například v příkladu v úvodu je <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda použita k načtení všech atributů `book` prvku.

Pokud zavoláte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu hned za <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metodou, vrátí se všechny atributy, které by se mohly zobrazit v dokumentu XML. Nicméně pokud zavoláte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu po jednom nebo více volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody, vrátí se atributy, které ještě nebyly ověřeny pro aktuální prvek.

> [!NOTE]
> Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metod <xref:System.Xml.Schema.XmlSchemaValidator> , <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>a třídy jsou závislé na ověřeném aktuálním kontextu. Další informace najdete v části "kontext ověření" v tomto tématu.

Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody naleznete v příkladu v úvodu. Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodě naleznete v referenční dokumentaci ke <xref:System.Xml.Schema.XmlSchemaValidator> třídě.

#### <a name="retrieving-unspecified-default-attributes"></a>Načítání nespecifikovaných výchozích atributů

<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda naplní <xref:System.Collections.ArrayList> zadané <xref:System.Xml.Schema.XmlSchemaAttribute> objekty pro všechny atributy výchozí hodnoty, které nebyly dříve ověřeny pomocí <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody v kontextu prvku. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla být volána po volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody u každého atributu v kontextu elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla být použita k určení, které výchozí atributy budou vloženy do ověřovaného dokumentu XML.

Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metodě naleznete v referenční dokumentaci ke <xref:System.Xml.Schema.XmlSchemaValidator> třídě.

### <a name="handling-schema-validation-events"></a>Zpracování událostí ověřování schématu

Upozornění ověřování schématu a chyby zjištěné během ověřování jsou zpracovávány <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> událostí <xref:System.Xml.Schema.XmlSchemaValidator> třídy.

Upozornění ověřování schématu <xref:System.Xml.Schema.XmlSeverityType> mají hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu mají <xref:System.Xml.Schema.XmlSeverityType> hodnotu. <xref:System.Xml.Schema.XmlSeverityType.Error> Pokud nebyla <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> přiřazena žádná <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.Schema.XmlSeverityType> hodnota, je vyvolána pro všechny chyby ověřování schématu s hodnotou <xref:System.Xml.Schema.XmlSeverityType.Error>. Nicméně <xref:System.Xml.Schema.XmlSchemaValidationException> se nevyvolá pro upozornění ověřování schématu s <xref:System.Xml.Schema.XmlSeverityType> hodnotou. <xref:System.Xml.Schema.XmlSeverityType.Warning>

Následuje příklad <xref:System.Xml.Schema.ValidationEventHandler> , který přijímá upozornění ověřování schématu a chyby zjištěné při ověřování schématu provedené z příkladu v úvodu.

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

Úplný příklad <xref:System.Xml.Schema.ValidationEventHandler>naleznete v příkladu v úvodu. Další informace naleznete v <xref:System.Xml.Schema.XmlSchemaInfo> referenční dokumentaci ke třídě.

## <a name="xmlschemavalidator-state-transition"></a>Přechod stavu XmlSchemaValidator

<xref:System.Xml.Schema.XmlSchemaValidator> Třída má definovaný přechod stavu, který vynutila sekvenci a výskyt volání v každé z metod, které slouží k ověření elementů, atributů a obsahu v XML informačním souboru.

Následující tabulka popisuje přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy a sekvenci a výskyt volání metody, které lze provést v každém stavu.

|Stav|Transition|
|-----------|----------------|
|Ověření|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>(<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; Toplevel *)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>Element <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; &#124;|
|Prvek|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsah\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A><br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124; obsahu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> \*|
|Obsah|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>Element <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; &#124;|

> [!NOTE]
> <xref:System.InvalidOperationException> Je vyvolána každou metodou v tabulce výše, pokud je volání metody provedeno v nesprávné sekvenci podle aktuálního stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.

Výše uvedená tabulka přechodu stavu používá interpunkční znaménka k popisu metod a dalších stavů, které mohou být volány pro každý stav přechodu stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy. Použité symboly jsou stejné symboly, které najdete v referenčních standardech XML pro definici typu dokumentu (DTD).

Následující tabulka popisuje, jak se symboly interpunkčních znamének v tabulce přechodu stavu nacházejí výše ovlivňují metody a další stavy, které mohou být volány pro každý stav v přechodu stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.

|Symbol|Popis|
|------------|-----------------|
|&#124;|Lze zavolat buď metodu, nebo stav (jeden před pruhový nebo ten).|
|?|Metoda nebo stav, který předchází otazník je volitelný, ale pokud je volána, lze ji volat pouze jednou.|
|*|Metoda nebo stav, který předchází symbolu * je volitelná a může být volána více než jednou.|

## <a name="validation-context"></a>Kontext ověřování

Metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy používané pro ověřování prvků, atributů a obsahu v XML XML, mění kontext ověření <xref:System.Xml.Schema.XmlSchemaValidator> objektu. Například <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> Metoda přeskočí ověření aktuálního obsahu prvku a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt pro ověření obsahu v kontextu nadřazeného elementu; je ekvivalentní k přeskočení ověřování pro všechny podřízené položky aktuálního prvku a následnému volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.

Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metod <xref:System.Xml.Schema.XmlSchemaValidator> , <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>a třídy jsou závislé na ověřeném aktuálním kontextu.

V následující tabulce jsou popsány výsledky volání těchto metod po volání jedné z metod <xref:System.Xml.Schema.XmlSchemaValidator> třídy používané pro ověřování prvků, atributů a obsahu v XML informačním souboru.

|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Pokud je volána <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> výchozí metoda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pole obsahující všechny globální prvky.<br /><br /> Pokud je pro inicializaci částečného ověřování <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> prvku volána <xref:System.Xml.Schema.XmlSchemaObject> přetížená metoda, která přijímá jako parametr, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému byl <xref:System.Xml.Schema.XmlSchemaValidator> objekt inicializován.|Pokud je volána <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> výchozí metoda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> Pokud <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> je volání metody, která <xref:System.Xml.Schema.XmlSchemaObject> přijímá jako parametr, volána k inicializaci částečného ověřování atributu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut, na který byl <xref:System.Xml.Schema.XmlSchemaValidator> objekt inicializován.|Přidá schéma k <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaValidator> objektu, pokud nemá žádné chyby předzpracování.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Pokud je kontextový prvek platný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávaných jako podřízené objekty kontextu elementu.<br /><br /> Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.|Pokud je kontextový prvek platný a pokud nebylo dříve provedeno žádné <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> volání, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam všech atributů definovaných v prvku kontextu.<br /><br /> Pokud některé atributy již byly ověřeny, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývajících atributů, které mají být ověřeny.<br /><br /> Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> opačném případě vrátí sekvenci prvků očekávanou jako první podřízený prvek kontextu.|Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> V <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> opačném případě vrátí seznam zbývajících atributů, které mají být ověřeny.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí seznam požadovaných a volitelných atributů, které se ještě ověřují pro prvek kontextu.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>vrátí prázdné pole.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Pokud je třída contentType elementu kontextu smíšená, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávaných v další pozici.<br /><br /> Pokud je třída contentType elementu kontextu typu TextOnly nebo prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> Pokud je objekt contentType elementu kontextu ElementOnly, vrátí <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sekvenci prvků očekávanou na další pozici, ale k chybě ověřování již došlo.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí seznam atributů elementu kontextu, které nejsou ověřeny.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Pokud je v tomto kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.<br /><br /> V opačném případě je chování <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Pokud je v tomto kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.<br /><br /> V opačném případě je chování <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>vrací sekvenci prvků očekávaných po elementu Context (možné na stejné úrovni).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí seznam atributů elementu kontextu, které nejsou ověřeny.<br /><br /> Pokud kontextový prvek nemá žádnou nadřazenou <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> položku, vrátí prázdný seznam (kontextový prvek je nadřazeným prvkem aktuálního prvku, který <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> byl volán).|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Stejné jako výše.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Vrátí prázdné pole.|Vrátí prázdné pole.|Stejné jako výše.|

> [!NOTE]
> Hodnoty vrácené různými vlastnostmi <xref:System.Xml.Schema.XmlSchemaValidator> třídy nejsou změněny voláním jakékoli metody ve výše uvedené tabulce.

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Schema.XmlSchemaValidator>
