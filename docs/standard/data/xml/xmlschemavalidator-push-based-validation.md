---
title: Přímé ověření XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: d5b2fe4325000023acc98580a2a6d014f56fecbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419106"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="8327d-102">Přímé ověření XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="8327d-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="8327d-103"><xref:System.Xml.Schema.XmlSchemaValidator>Třída poskytuje účinný a vysoce výkonný mechanismus pro ověřování dat XML proti schématům XML ve způsobu založeném na nabízených oznámeních.</span><span class="sxs-lookup"><span data-stu-id="8327d-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="8327d-104">Například <xref:System.Xml.Schema.XmlSchemaValidator> Třída umožňuje ověřit místně XML informační sadu bez nutnosti jejich serializace jako dokument XML a pak znovu analyzovat dokument s použitím ověřování XML Reader.</span><span class="sxs-lookup"><span data-stu-id="8327d-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="8327d-105"><xref:System.Xml.Schema.XmlSchemaValidator>Třída se dá použít v pokročilých scénářích, jako je vytváření ověřovacích modulů přes vlastní zdroje dat XML, nebo jako způsob, jak vytvořit ověřovací ZAPISOVAČ XML.</span><span class="sxs-lookup"><span data-stu-id="8327d-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="8327d-106">Následuje příklad použití <xref:System.Xml.Schema.XmlSchemaValidator> třídy k ověření `contosoBooks.xml` souboru proti `contosoBooks.xsd` schématu.</span><span class="sxs-lookup"><span data-stu-id="8327d-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="8327d-107">V příkladu se používá <xref:System.Xml.Serialization.XmlSerializer> třída k deserializaci `contosoBooks.xml` souboru a předání hodnoty uzlů do metod <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="8327d-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="8327d-108">Tento příklad se používá v celém oddílu tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8327d-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="8327d-109">Příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="8327d-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="8327d-110">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="8327d-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="8327d-111">Ověřování dat XML pomocí XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="8327d-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="8327d-112">Chcete-li zahájit ověřování XML informační sady, je nutné nejprve inicializovat novou instanci <xref:System.Xml.Schema.XmlSchemaValidator> třídy pomocí <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8327d-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="8327d-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>Konstruktor přebírá <xref:System.Xml.XmlNameTable> <xref:System.Xml.Schema.XmlSchemaSet> objekty, a <xref:System.Xml.XmlNamespaceManager> jako parametry a jako <xref:System.Xml.Schema.XmlSchemaValidationFlags> hodnotu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="8327d-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="8327d-114"><xref:System.Xml.XmlNameTable>Objekt se používá k atomizovat dobře známých řetězců oboru názvů, jako je například obor názvů schématu, obor názvů XML a tak dále, a je předán <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metodě při ověřování jednoduchého obsahu.</span><span class="sxs-lookup"><span data-stu-id="8327d-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="8327d-115"><xref:System.Xml.Schema.XmlSchemaSet>Objekt obsahuje schémata XML sloužící k ověření XML informační sady.</span><span class="sxs-lookup"><span data-stu-id="8327d-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="8327d-116"><xref:System.Xml.XmlNamespaceManager>Objekt se používá k překladu oborů názvů zjištěných během ověřování.</span><span class="sxs-lookup"><span data-stu-id="8327d-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="8327d-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags>Hodnota se používá k zakázání určitých funkcí ověřování.</span><span class="sxs-lookup"><span data-stu-id="8327d-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="8327d-118">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci třídy.</span><span class="sxs-lookup"><span data-stu-id="8327d-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="8327d-119">Inicializuje se ověřování.</span><span class="sxs-lookup"><span data-stu-id="8327d-119">Initializing Validation</span></span>

<span data-ttu-id="8327d-120">Po <xref:System.Xml.Schema.XmlSchemaValidator> sestavení objektu jsou k dispozici dvě přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, které se používají k inicializaci stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="8327d-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="8327d-121">Níže jsou uvedené dvě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8327d-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="8327d-122">Výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt do svého počátečního stavu a přetíženou <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metodu, která přijímá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt do svého počátečního stavu pro částečné ověření.</span><span class="sxs-lookup"><span data-stu-id="8327d-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="8327d-123">Obě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody lze volat pouze ihned po <xref:System.Xml.Schema.XmlSchemaValidator> sestavení objektu nebo po volání <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> .</span><span class="sxs-lookup"><span data-stu-id="8327d-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="8327d-124">Příklad metody naleznete v <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="8327d-125">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodě naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="8327d-126">Částečné ověření</span><span class="sxs-lookup"><span data-stu-id="8327d-126">Partial Validation</span></span>

<span data-ttu-id="8327d-127"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>Metoda, která přijímá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt do svého počátečního stavu pro částečné ověření.</span><span class="sxs-lookup"><span data-stu-id="8327d-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="8327d-128">V následujícím příkladu <xref:System.Xml.Schema.XmlSchemaObject> je inicializováno pro částečné ověřování pomocí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8327d-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8327d-129">`orderNumber`Prvek schématu je předán výběrem elementu schématu <xref:System.Xml.XmlQualifiedName> v <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekci vrácené <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> vlastností <xref:System.Xml.Schema.XmlSchemaSet> objektu.</span><span class="sxs-lookup"><span data-stu-id="8327d-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="8327d-130"><xref:System.Xml.Schema.XmlSchemaValidator>Objekt potom ověří tento konkrétní element.</span><span class="sxs-lookup"><span data-stu-id="8327d-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

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

<span data-ttu-id="8327d-131">Příklad má jako vstup následující schéma XML.</span><span class="sxs-lookup"><span data-stu-id="8327d-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="8327d-132">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodě naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="8327d-133">Přidání dalších schémat</span><span class="sxs-lookup"><span data-stu-id="8327d-133">Adding Additional Schemas</span></span>

<span data-ttu-id="8327d-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Metoda <xref:System.Xml.Schema.XmlSchemaValidator> třídy slouží k přidání schématu XML do sady schémat používaných při ověřování.</span><span class="sxs-lookup"><span data-stu-id="8327d-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="8327d-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Metoda může být použita k simulaci efektu zaznamenání vloženého schématu XML do OVĚŘOVANÉ XML informační sady.</span><span class="sxs-lookup"><span data-stu-id="8327d-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="8327d-136">Cílový obor názvů <xref:System.Xml.Schema.XmlSchema> parametru nemůže odpovídat žádnému elementu nebo atributu, který je již v objektu nalezen <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="8327d-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="8327d-137">Pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> hodnota nebyla předána jako parametr <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda neprovede žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="8327d-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="8327d-138">Výsledek <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody závisí na ověření aktuálního kontextu uzlu XML.</span><span class="sxs-lookup"><span data-stu-id="8327d-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="8327d-139">Další informace o kontextech ověřování naleznete v části "kontext ověření" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8327d-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="8327d-140">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metodě naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="8327d-141">Ověřování elementů, atributů a obsahu</span><span class="sxs-lookup"><span data-stu-id="8327d-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="8327d-142"><xref:System.Xml.Schema.XmlSchemaValidator>Třída poskytuje několik metod, které slouží k ověření elementů, atributů a obsahu v XML informačním souboru pro schémata XML.</span><span class="sxs-lookup"><span data-stu-id="8327d-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="8327d-143">Následující tabulka popisuje každou z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="8327d-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="8327d-144">Metoda</span><span class="sxs-lookup"><span data-stu-id="8327d-144">Method</span></span>|<span data-ttu-id="8327d-145">Popis</span><span class="sxs-lookup"><span data-stu-id="8327d-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="8327d-146">Ověří název elementu v aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="8327d-147">Ověří atribut v kontextu aktuálního prvku nebo <xref:System.Xml.Schema.XmlSchemaAttribute> objektu předaného jako parametr <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="8327d-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="8327d-148">Ověřuje, zda jsou přítomny všechny požadované atributy v kontextu elementu, a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt k ověření podřízeného obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="8327d-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="8327d-149">Ověří, zda je povolen text v kontextu aktuálního prvku, a nashromáždí text pro ověření, pokud má aktuální prvek jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="8327d-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="8327d-150">Ověří, zda je v aktuálním kontextu prvku povoleno prázdné místo a zda má aktuální prvek jednoduchý obsah, a nashromáždí prázdný prostor pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="8327d-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="8327d-151">Ověřuje, zda je textový obsah elementu platný vzhledem k jeho datovému typu pro prvky s jednoduchým obsahem a ověřuje, zda je obsah aktuálního prvku dokončen pro prvky se složitým obsahem.</span><span class="sxs-lookup"><span data-stu-id="8327d-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="8327d-152">Přeskočí ověřování aktuálního obsahu elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt k ověření obsahu v kontextu nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="8327d-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="8327d-153">Ukončí ověřování a zkontroluje omezení identity pro celý dokument XML, pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> je nastavena možnost ověřování.</span><span class="sxs-lookup"><span data-stu-id="8327d-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="8327d-154"><xref:System.Xml.Schema.XmlSchemaValidator>Třída má definovaný přechod stavu, který vynutila sekvenci a výskyt volání každé z metod popsaných v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="8327d-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="8327d-155">Konkrétní přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy je popsán v tomto tématu v části "přechod stavu XmlSchemaValidator".</span><span class="sxs-lookup"><span data-stu-id="8327d-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="8327d-156">Příklad metod, které slouží k ověření elementů, atributů a obsahu v informační příručce XML, naleznete v příkladu v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="8327d-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="8327d-157">Další informace o těchto metodách naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="8327d-158">Ověřování obsahu pomocí XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="8327d-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="8327d-159"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Lze použít k předání hodnoty atributu, textu nebo prázdných uzlů jako typů modulu CLR (Common Language Runtime), které jsou kompatibilní s typem jazyka XML Schema Definition Language (XSD) atributu, textu nebo prázdného uzlu.</span><span class="sxs-lookup"><span data-stu-id="8327d-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="8327d-160"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Je užitečné, pokud je hodnota CLR uzlu, textu nebo prázdného prostoru již k dispozici, a nepoužívejte náklady na jejich převod na `string` a pak znovu znovu analyzovat pro ověření.</span><span class="sxs-lookup"><span data-stu-id="8327d-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="8327d-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>Metody, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> a <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> jsou přetížené a přijímají hodnotu atributu, textu nebo prázdných uzlů jako `string` nebo <xref:System.Xml.Schema.XmlValueGetter> `delegate` .</span><span class="sxs-lookup"><span data-stu-id="8327d-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="8327d-162">Následující metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy přijímají <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="8327d-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="8327d-163">Následuje příklad, který je <xref:System.Xml.Schema.XmlValueGetter> `delegate` povedený z <xref:System.Xml.Schema.XmlSchemaValidator> příkladu třídy v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="8327d-164"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Vrátí hodnotu atributu jako <xref:System.DateTime> objekt.</span><span class="sxs-lookup"><span data-stu-id="8327d-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="8327d-165">Chcete-li ověřit <xref:System.DateTime> <xref:System.Xml.Schema.XmlValueGetter> , že objekt vrácený, <xref:System.Xml.Schema.XmlSchemaValidator> objekt nejprve převede na ValueType (ValueType je výchozí mapování CLR pro typ XSD) pro datový typ atributu a poté zkontroluje charakteristiky převedené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8327d-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

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

<span data-ttu-id="8327d-166">Úplný příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate` naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="8327d-167">Další informace o naleznete v <xref:System.Xml.Schema.XmlValueGetter> `delegate` <xref:System.Xml.Schema.XmlValueGetter> <xref:System.Xml.Schema.XmlSchemaValidator> dokumentaci ke třídě a referenční dokumentaci k ní.</span><span class="sxs-lookup"><span data-stu-id="8327d-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="8327d-168">Po ověření schématu – informace</span><span class="sxs-lookup"><span data-stu-id="8327d-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="8327d-169"><xref:System.Xml.Schema.XmlSchemaInfo>Třída reprezentuje některé z informací o ověřování po schématu, které jsou v uzlu XML ověřené <xref:System.Xml.Schema.XmlSchemaValidator> třídou.</span><span class="sxs-lookup"><span data-stu-id="8327d-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="8327d-170">Různé metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy přijímají <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako volitelný parametr, ( `null` ) `out` .</span><span class="sxs-lookup"><span data-stu-id="8327d-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="8327d-171">Po úspěšném ověření <xref:System.Xml.Schema.XmlSchemaInfo> jsou vlastnosti objektu nastaveny s výsledky ověření.</span><span class="sxs-lookup"><span data-stu-id="8327d-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="8327d-172">Například po úspěšném ověření atributu pomocí <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody je <xref:System.Xml.Schema.XmlSchemaInfo> objekt (je-li zadán) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A> , <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A> , <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> vlastností nastaven s výsledky ověření.</span><span class="sxs-lookup"><span data-stu-id="8327d-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="8327d-173">Následující <xref:System.Xml.Schema.XmlSchemaValidator> metody třídy přijímají <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="8327d-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="8327d-174">Úplný příklad této <xref:System.Xml.Schema.XmlSchemaInfo> třídy naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="8327d-175">Další informace o <xref:System.Xml.Schema.XmlSchemaInfo> třídě naleznete v <xref:System.Xml.Schema.XmlSchemaInfo> referenční dokumentaci třídy.</span><span class="sxs-lookup"><span data-stu-id="8327d-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="8327d-176">Načítání očekávaných částic, atributů a nespecifikovaných výchozích atributů</span><span class="sxs-lookup"><span data-stu-id="8327d-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="8327d-177"><xref:System.Xml.Schema.XmlSchemaValidator>Třída poskytuje <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> pro načtení očekávaných částic, atributů a nespecifikovaných výchozích atributů v aktuálním kontextu ověřování.</span><span class="sxs-lookup"><span data-stu-id="8327d-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="8327d-178">Načítání očekávaných částic</span><span class="sxs-lookup"><span data-stu-id="8327d-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="8327d-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Metoda vrací pole objektů, které <xref:System.Xml.Schema.XmlSchemaParticle> obsahují očekávané částice v kontextu aktuálního prvku.</span><span class="sxs-lookup"><span data-stu-id="8327d-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="8327d-180">Platné částice, které mohou být vráceny <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodou, jsou instance <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAny> třídy a.</span><span class="sxs-lookup"><span data-stu-id="8327d-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="8327d-181">Když je kompozice modelu obsahu `xs:sequence` , vrátí se pouze další částice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="8327d-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="8327d-182">Pokud je kompozice modelu obsahu `xs:all` nebo a `xs:choice` , pak jsou vráceny všechny platné částice, které by mohly následovat v kontextu aktuálního prvku.</span><span class="sxs-lookup"><span data-stu-id="8327d-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="8327d-183">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> je metoda volána bezprostředně po volání <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí všechny globální prvky.</span><span class="sxs-lookup"><span data-stu-id="8327d-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="8327d-184">Například v schématu XML schématu (XSD) a dokumentu XML, který následuje, je po ověření `book` elementu `book` element prvkem aktuální kontext prvku.</span><span class="sxs-lookup"><span data-stu-id="8327d-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="8327d-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Metoda vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `title` element.</span><span class="sxs-lookup"><span data-stu-id="8327d-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="8327d-186">Když je kontext ověření `title` element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="8327d-187">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> je metoda volána po `title` ověření prvku, ale před `description` ověřením elementu, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `description` prvek.</span><span class="sxs-lookup"><span data-stu-id="8327d-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="8327d-188">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> je metoda volána po `description` ověření elementu, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaAny> objekt reprezentující zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="8327d-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

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

 <span data-ttu-id="8327d-189">Příklad má jako vstup následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="8327d-189">The example takes the following XML as input:</span></span>

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

<span data-ttu-id="8327d-190">Příklad má jako vstup následující schéma XSD:</span><span class="sxs-lookup"><span data-stu-id="8327d-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="8327d-191">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metod, a <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na ověřeném aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="8327d-192">Další informace najdete v části "kontext ověření" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8327d-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="8327d-193">Příklad metody naleznete v <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="8327d-194">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodě naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="8327d-195">Načítání očekávaných atributů</span><span class="sxs-lookup"><span data-stu-id="8327d-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="8327d-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Metoda vrací pole objektů, které <xref:System.Xml.Schema.XmlSchemaAttribute> obsahují očekávané atributy v kontextu aktuálního prvku.</span><span class="sxs-lookup"><span data-stu-id="8327d-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="8327d-197">Například v příkladu v úvodu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> je metoda použita k načtení všech atributů `book` prvku.</span><span class="sxs-lookup"><span data-stu-id="8327d-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="8327d-198">Pokud zavoláte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu hned za <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metodou, vrátí se všechny atributy, které by se mohly zobrazit v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="8327d-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="8327d-199">Nicméně pokud zavoláte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu po jednom nebo více volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody, vrátí se atributy, které ještě nebyly ověřeny pro aktuální prvek.</span><span class="sxs-lookup"><span data-stu-id="8327d-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="8327d-200">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metod, a <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na ověřeném aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="8327d-201">Další informace najdete v části "kontext ověření" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8327d-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="8327d-202">Příklad metody naleznete v <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="8327d-203">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodě naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="8327d-204">Načítání nespecifikovaných výchozích atributů</span><span class="sxs-lookup"><span data-stu-id="8327d-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="8327d-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Metoda naplní <xref:System.Collections.ArrayList> zadané <xref:System.Xml.Schema.XmlSchemaAttribute> objekty pro všechny atributy výchozí hodnoty, které nebyly dříve ověřeny pomocí <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody v kontextu prvku.</span><span class="sxs-lookup"><span data-stu-id="8327d-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="8327d-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Metoda by měla být volána po volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody u každého atributu v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="8327d-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="8327d-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Metoda by měla být použita k určení, které výchozí atributy budou vloženy do ověřovaného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="8327d-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="8327d-208">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metodě naleznete v <xref:System.Xml.Schema.XmlSchemaValidator> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="8327d-209">Zpracování událostí ověřování schématu</span><span class="sxs-lookup"><span data-stu-id="8327d-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="8327d-210">Upozornění ověřování schématu a chyby zjištěné během ověřování jsou zpracovávány <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> událostí <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="8327d-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="8327d-211">Upozornění ověřování schématu mají <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu mají <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error> .</span><span class="sxs-lookup"><span data-stu-id="8327d-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="8327d-212">Pokud nebyla <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> přiřazena žádná <xref:System.Xml.Schema.XmlSchemaValidationException> hodnota, je vyvolána pro všechny chyby ověřování schématu s <xref:System.Xml.Schema.XmlSeverityType> hodnotou <xref:System.Xml.Schema.XmlSeverityType.Error> .</span><span class="sxs-lookup"><span data-stu-id="8327d-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="8327d-213">Nicméně <xref:System.Xml.Schema.XmlSchemaValidationException> se nevyvolá pro upozornění ověřování schématu s <xref:System.Xml.Schema.XmlSeverityType> hodnotou <xref:System.Xml.Schema.XmlSeverityType.Warning> .</span><span class="sxs-lookup"><span data-stu-id="8327d-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="8327d-214">Následuje příklad <xref:System.Xml.Schema.ValidationEventHandler> , který přijímá upozornění ověřování schématu a chyby zjištěné při ověřování schématu provedené z příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

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

<span data-ttu-id="8327d-215">Úplný příklad <xref:System.Xml.Schema.ValidationEventHandler> naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="8327d-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="8327d-216">Další informace naleznete v <xref:System.Xml.Schema.XmlSchemaInfo> referenční dokumentaci ke třídě.</span><span class="sxs-lookup"><span data-stu-id="8327d-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="8327d-217">Přechod stavu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="8327d-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="8327d-218"><xref:System.Xml.Schema.XmlSchemaValidator>Třída má definovaný přechod stavu, který vynutila sekvenci a výskyt volání v každé z metod, které slouží k ověření elementů, atributů a obsahu v XML informačním souboru.</span><span class="sxs-lookup"><span data-stu-id="8327d-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="8327d-219">Následující tabulka popisuje přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy a sekvenci a výskyt volání metody, které lze provést v každém stavu.</span><span class="sxs-lookup"><span data-stu-id="8327d-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="8327d-220">State</span><span class="sxs-lookup"><span data-stu-id="8327d-220">State</span></span>|<span data-ttu-id="8327d-221">Transition</span><span class="sxs-lookup"><span data-stu-id="8327d-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="8327d-222">Ověření</span><span class="sxs-lookup"><span data-stu-id="8327d-222">Validate</span></span>|<span data-ttu-id="8327d-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; Toplevel \*)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="8327d-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="8327d-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="8327d-224">TopLevel</span></span>|<span data-ttu-id="8327d-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>Element &#124; &#124;</span><span class="sxs-lookup"><span data-stu-id="8327d-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="8327d-226">Prvek</span><span class="sxs-lookup"><span data-stu-id="8327d-226">Element</span></span>|<span data-ttu-id="8327d-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* ( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsah \* )?</span><span class="sxs-lookup"><span data-stu-id="8327d-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="8327d-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="8327d-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="8327d-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="8327d-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="8327d-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124; obsahu</span><span class="sxs-lookup"><span data-stu-id="8327d-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="8327d-231">Obsah</span><span class="sxs-lookup"><span data-stu-id="8327d-231">Content</span></span>|<span data-ttu-id="8327d-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>Element &#124; &#124;</span><span class="sxs-lookup"><span data-stu-id="8327d-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="8327d-233"><xref:System.InvalidOperationException>Je vyvolána každou metodou v tabulce výše, pokud je volání metody provedeno v nesprávné sekvenci podle aktuálního stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="8327d-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="8327d-234">Výše uvedená tabulka přechodu stavu používá interpunkční znaménka k popisu metod a dalších stavů, které mohou být volány pro každý stav přechodu stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="8327d-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="8327d-235">Použité symboly jsou stejné symboly, které najdete v referenčních standardech XML pro definici typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="8327d-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="8327d-236">Následující tabulka popisuje, jak se symboly interpunkčních znamének v tabulce přechodu stavu nacházejí výše ovlivňují metody a další stavy, které mohou být volány pro každý stav v přechodu stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="8327d-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="8327d-237">Symbol</span><span class="sxs-lookup"><span data-stu-id="8327d-237">Symbol</span></span>|<span data-ttu-id="8327d-238">Popis</span><span class="sxs-lookup"><span data-stu-id="8327d-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="8327d-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="8327d-239">&#124;</span></span>|<span data-ttu-id="8327d-240">Lze zavolat buď metodu, nebo stav (jeden před pruhový nebo ten).</span><span class="sxs-lookup"><span data-stu-id="8327d-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="8327d-241">?</span><span class="sxs-lookup"><span data-stu-id="8327d-241">?</span></span>|<span data-ttu-id="8327d-242">Metoda nebo stav, který předchází otazník je volitelný, ale pokud je volána, lze ji volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="8327d-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|\*|<span data-ttu-id="8327d-243">Metoda nebo stav, který předchází \* symbolu je volitelná a může být volána více než jednou.</span><span class="sxs-lookup"><span data-stu-id="8327d-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="8327d-244">Kontext ověřování</span><span class="sxs-lookup"><span data-stu-id="8327d-244">Validation Context</span></span>

<span data-ttu-id="8327d-245">Metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy používané pro ověřování prvků, atributů a obsahu v XML XML, mění kontext ověření <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="8327d-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="8327d-246">Například <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> Metoda přeskočí ověření aktuálního obsahu prvku a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt k ověření obsahu v kontextu nadřazeného elementu; je ekvivalentní k přeskočení ověřování pro všechny podřízené položky aktuálního prvku a následnému volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8327d-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="8327d-247">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metod, a <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na ověřeném aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="8327d-248">V následující tabulce jsou popsány výsledky volání těchto metod po volání jedné z metod <xref:System.Xml.Schema.XmlSchemaValidator> třídy používané pro ověřování prvků, atributů a obsahu v XML informačním souboru.</span><span class="sxs-lookup"><span data-stu-id="8327d-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="8327d-249">Metoda</span><span class="sxs-lookup"><span data-stu-id="8327d-249">Method</span></span>|<span data-ttu-id="8327d-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="8327d-250">GetExpectedParticles</span></span>|<span data-ttu-id="8327d-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="8327d-251">GetExpectedAttributes</span></span>|<span data-ttu-id="8327d-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="8327d-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="8327d-253">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> je volána výchozí metoda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pole obsahující všechny globální prvky.</span><span class="sxs-lookup"><span data-stu-id="8327d-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="8327d-254">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> <xref:System.Xml.Schema.XmlSchemaObject> je pro inicializaci částečného ověřování prvku volána přetížená metoda, která přijímá jako parametr, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému <xref:System.Xml.Schema.XmlSchemaValidator> byl objekt inicializován.</span><span class="sxs-lookup"><span data-stu-id="8327d-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="8327d-255">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> je volána výchozí metoda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="8327d-256">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> je volání metody, která přijímá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, volána k inicializaci částečného ověřování atributu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut, na který <xref:System.Xml.Schema.XmlSchemaValidator> byl objekt inicializován.</span><span class="sxs-lookup"><span data-stu-id="8327d-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="8327d-257">Přidá schéma k objektu, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaValidator> Pokud nemá žádné chyby předzpracování.</span><span class="sxs-lookup"><span data-stu-id="8327d-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="8327d-258">Pokud je kontextový prvek platný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávaných jako podřízené objekty kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="8327d-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="8327d-259">Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="8327d-260">Pokud je kontextový prvek platný a pokud nebylo <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> dříve provedeno žádné volání, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam všech atributů definovaných v prvku kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="8327d-261">Pokud některé atributy již byly ověřeny, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývajících atributů, které mají být ověřeny.</span><span class="sxs-lookup"><span data-stu-id="8327d-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="8327d-262">Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="8327d-263">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="8327d-264">Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="8327d-265">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávanou jako první podřízený prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="8327d-266">Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="8327d-267">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývajících atributů, které mají být ověřeny.</span><span class="sxs-lookup"><span data-stu-id="8327d-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="8327d-268">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="8327d-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="8327d-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí seznam požadovaných a volitelných atributů, které se ještě ověřují pro prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="8327d-271">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="8327d-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="8327d-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="8327d-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="8327d-274">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="8327d-275">Pokud je třída contentType elementu kontextu smíšená, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávaných v další pozici.</span><span class="sxs-lookup"><span data-stu-id="8327d-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="8327d-276">Pokud je třída contentType elementu kontextu typu TextOnly nebo prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="8327d-277">Pokud je objekt contentType elementu kontextu ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávanou na další pozici, ale k chybě ověřování již došlo.</span><span class="sxs-lookup"><span data-stu-id="8327d-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="8327d-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí seznam atributů elementu kontextu, které nejsou ověřeny.</span><span class="sxs-lookup"><span data-stu-id="8327d-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="8327d-279">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="8327d-280">Pokud je v tomto kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="8327d-281">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> je chování metody stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .</span><span class="sxs-lookup"><span data-stu-id="8327d-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="8327d-282">Pokud je v tomto kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="8327d-283">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> je chování metody stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .</span><span class="sxs-lookup"><span data-stu-id="8327d-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="8327d-284">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="8327d-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>vrací sekvenci prvků očekávaných po elementu Context (možné na stejné úrovni).</span><span class="sxs-lookup"><span data-stu-id="8327d-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="8327d-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Vrátí seznam atributů elementu kontextu, které nejsou ověřeny.</span><span class="sxs-lookup"><span data-stu-id="8327d-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="8327d-287">Pokud kontextový prvek nemá žádnou nadřazenou položku, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdný seznam (kontextový prvek je nadřazeným prvkem aktuálního prvku, který <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> byl volán).</span><span class="sxs-lookup"><span data-stu-id="8327d-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="8327d-288">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="8327d-289">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="8327d-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="8327d-290">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="8327d-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="8327d-291">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="8327d-292">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-292">Returns an empty array.</span></span>|<span data-ttu-id="8327d-293">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="8327d-293">Returns an empty array.</span></span>|<span data-ttu-id="8327d-294">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="8327d-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="8327d-295">Hodnoty vrácené různými vlastnostmi <xref:System.Xml.Schema.XmlSchemaValidator> třídy nejsou změněny voláním jakékoli metody ve výše uvedené tabulce.</span><span class="sxs-lookup"><span data-stu-id="8327d-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="8327d-296">Viz také</span><span class="sxs-lookup"><span data-stu-id="8327d-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
