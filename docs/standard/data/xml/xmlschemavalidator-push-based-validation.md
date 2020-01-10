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
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="09621-102">Přímé ověření XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="09621-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="09621-103">Třída <xref:System.Xml.Schema.XmlSchemaValidator> poskytuje účinný a vysoce výkonný mechanismus pro ověřování dat XML proti schématům XML ve způsobu založeném na nabízených oznámeních.</span><span class="sxs-lookup"><span data-stu-id="09621-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="09621-104">Například třída <xref:System.Xml.Schema.XmlSchemaValidator> umožňuje ověřit místní informační sadu XML bez nutnosti jejich serializace jako dokument XML a pak znovu analyzovat dokument pomocí ověřování XML Reader.</span><span class="sxs-lookup"><span data-stu-id="09621-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="09621-105">Třídu <xref:System.Xml.Schema.XmlSchemaValidator> lze použít v pokročilých scénářích, jako je vytváření ověřovacích modulů přes vlastní zdroje dat XML, nebo jako způsob sestavení ověřování XML Writer.</span><span class="sxs-lookup"><span data-stu-id="09621-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="09621-106">Následuje příklad použití třídy <xref:System.Xml.Schema.XmlSchemaValidator> k ověření souboru `contosoBooks.xml` proti schématu `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="09621-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="09621-107">V příkladu se používá třída <xref:System.Xml.Serialization.XmlSerializer> k deserializaci `contosoBooks.xml` souboru a předání hodnoty uzlů do metod třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="09621-108">Tento příklad se používá v celém oddílu tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="09621-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="09621-109">V příkladu se jako vstup používá soubor `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="09621-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="09621-110">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="09621-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="09621-111">Ověřování dat XML pomocí XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="09621-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="09621-112">Chcete-li zahájit ověřování XML informační sady, je nutné nejprve inicializovat novou instanci třídy <xref:System.Xml.Schema.XmlSchemaValidator> pomocí konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="09621-113">Konstruktor <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> přebírá objekty <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>a <xref:System.Xml.XmlNamespaceManager> jako parametry a také <xref:System.Xml.Schema.XmlSchemaValidationFlags> hodnota jako parametr.</span><span class="sxs-lookup"><span data-stu-id="09621-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="09621-114">Objekt <xref:System.Xml.XmlNameTable> slouží k atomizovatí známých řetězců oboru názvů, jako je například obor názvů schématu, obor názvů XML a tak dále, a je předán metodě <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> při ověřování jednoduchého obsahu.</span><span class="sxs-lookup"><span data-stu-id="09621-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="09621-115">Objekt <xref:System.Xml.Schema.XmlSchemaSet> obsahuje schémata XML sloužící k ověření XML informační sady.</span><span class="sxs-lookup"><span data-stu-id="09621-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="09621-116">Objekt <xref:System.Xml.XmlNamespaceManager> se používá k překladu oborů názvů zjištěných během ověřování.</span><span class="sxs-lookup"><span data-stu-id="09621-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="09621-117">Hodnota <xref:System.Xml.Schema.XmlSchemaValidationFlags> slouží k zakázání určitých funkcí ověřování.</span><span class="sxs-lookup"><span data-stu-id="09621-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="09621-118">Další informace o konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="09621-119">Inicializuje se ověřování.</span><span class="sxs-lookup"><span data-stu-id="09621-119">Initializing Validation</span></span>

<span data-ttu-id="09621-120">Po sestavení objektu <xref:System.Xml.Schema.XmlSchemaValidator> jsou k dispozici dvě přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, které slouží k inicializaci stavu objektu <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="09621-121">Níže jsou uvedené dvě metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="09621-122">Výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt do svého počátečního stavu a přetíženou metodu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, která převezme <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, inicializuje objekt <xref:System.Xml.Schema.XmlSchemaValidator> na počáteční stav pro částečné ověření.</span><span class="sxs-lookup"><span data-stu-id="09621-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="09621-123">Obě metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> mohou být volány pouze ihned po sestavení <xref:System.Xml.Schema.XmlSchemaValidator> objektu nebo po volání <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="09621-124">Příklad metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="09621-125">Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="09621-126">Částečné ověření</span><span class="sxs-lookup"><span data-stu-id="09621-126">Partial Validation</span></span>

<span data-ttu-id="09621-127">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje objekt <xref:System.Xml.Schema.XmlSchemaValidator> na počáteční stav pro částečné ověření.</span><span class="sxs-lookup"><span data-stu-id="09621-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="09621-128">V následujícím příkladu je inicializována <xref:System.Xml.Schema.XmlSchemaObject> pro částečné ověřování pomocí metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09621-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="09621-129">`orderNumber` prvek schématu je předán výběrem elementu schématu pomocí <xref:System.Xml.XmlQualifiedName> v kolekci <xref:System.Xml.Schema.XmlSchemaObjectTable>, kterou vrátí vlastnost <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> objektu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="09621-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="09621-130">Objekt <xref:System.Xml.Schema.XmlSchemaValidator> potom ověří tento konkrétní element.</span><span class="sxs-lookup"><span data-stu-id="09621-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

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

<span data-ttu-id="09621-131">Příklad má jako vstup následující schéma XML.</span><span class="sxs-lookup"><span data-stu-id="09621-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="09621-132">Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="09621-133">Přidání dalších schémat</span><span class="sxs-lookup"><span data-stu-id="09621-133">Adding Additional Schemas</span></span>

<span data-ttu-id="09621-134">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> se používá k přidání schématu XML do sady schémat používaných při ověřování.</span><span class="sxs-lookup"><span data-stu-id="09621-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="09621-135">Metodu <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> lze použít k simulaci efektu zaznamenání vloženého schématu XML v ověřované XML informační službě.</span><span class="sxs-lookup"><span data-stu-id="09621-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="09621-136">Cílový obor názvů parametru <xref:System.Xml.Schema.XmlSchema> nemůže odpovídat žádnému elementu nebo atributu, který je již nalezen v objektu <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="09621-137">Pokud hodnota <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> nebyla předána jako parametr konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> neprovede žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="09621-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="09621-138">Výsledek metody <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> je závislý na ověření aktuálního kontextu uzlu XML.</span><span class="sxs-lookup"><span data-stu-id="09621-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="09621-139">Další informace o kontextech ověřování naleznete v části "kontext ověření" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="09621-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="09621-140">Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="09621-141">Ověřování elementů, atributů a obsahu</span><span class="sxs-lookup"><span data-stu-id="09621-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="09621-142">Třída <xref:System.Xml.Schema.XmlSchemaValidator> poskytuje několik metod, které slouží k ověření elementů, atributů a obsahu v XML informačním souboru pro schémata XML.</span><span class="sxs-lookup"><span data-stu-id="09621-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="09621-143">Následující tabulka popisuje každou z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="09621-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="09621-144">Metoda</span><span class="sxs-lookup"><span data-stu-id="09621-144">Method</span></span>|<span data-ttu-id="09621-145">Popis</span><span class="sxs-lookup"><span data-stu-id="09621-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="09621-146">Ověří název elementu v aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="09621-147">Ověří atribut v kontextu aktuálního prvku nebo proti <xref:System.Xml.Schema.XmlSchemaAttribute>mu objektu předanému jako parametr metodě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="09621-148">Ověřuje, zda jsou přítomny všechny požadované atributy v kontextu elementu, a připraví objekt <xref:System.Xml.Schema.XmlSchemaValidator> k ověření podřízeného obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="09621-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="09621-149">Ověří, zda je povolen text v kontextu aktuálního prvku, a nashromáždí text pro ověření, pokud má aktuální prvek jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="09621-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="09621-150">Ověří, zda je v aktuálním kontextu prvku povoleno prázdné místo a zda má aktuální prvek jednoduchý obsah, a nashromáždí prázdný prostor pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="09621-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="09621-151">Ověřuje, zda je textový obsah elementu platný vzhledem k jeho datovému typu pro prvky s jednoduchým obsahem a ověřuje, zda je obsah aktuálního prvku dokončen pro prvky se složitým obsahem.</span><span class="sxs-lookup"><span data-stu-id="09621-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="09621-152">Přeskočí ověřování aktuálního obsahu elementu a připraví objekt <xref:System.Xml.Schema.XmlSchemaValidator> k ověření obsahu v kontextu nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="09621-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="09621-153">Ukončí ověřování a zkontroluje omezení identity pro celý dokument XML, pokud je nastavena možnost ověření <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints>.</span><span class="sxs-lookup"><span data-stu-id="09621-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="09621-154">Třída <xref:System.Xml.Schema.XmlSchemaValidator> má definovaný přechod stavu, který vynutila sekvenci a výskyt volání každé z metod popsaných v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="09621-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="09621-155">Konkrétní přechod stavu třídy <xref:System.Xml.Schema.XmlSchemaValidator> je popsán v tomto tématu v části "přechod stavu XmlSchemaValidator".</span><span class="sxs-lookup"><span data-stu-id="09621-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="09621-156">Příklad metod, které slouží k ověření elementů, atributů a obsahu v informační příručce XML, naleznete v příkladu v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="09621-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="09621-157">Další informace o těchto metodách naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="09621-158">Ověřování obsahu pomocí XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="09621-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="09621-159"><xref:System.Xml.Schema.XmlValueGetter>`delegate` lze použít k předání hodnoty atributu, textu nebo prázdných uzlů jako typů modulu CLR (Common Language Runtime), které jsou kompatibilní s typem jazyka XML Schema Definition Language (XSD) atributu, textu nebo bílého prostoru.</span><span class="sxs-lookup"><span data-stu-id="09621-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="09621-160"><xref:System.Xml.Schema.XmlValueGetter>`delegate` je užitečné, pokud je hodnota CLR pro uzel, text nebo prázdné místo v uzlu již k dispozici, a vyhněte se nákladům na jejich převod na `string` a pak znovu znovu analyzovat pro ověření.</span><span class="sxs-lookup"><span data-stu-id="09621-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="09621-161">Metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>a <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> jsou přetížené a přijímají hodnotu atributu, textu nebo prázdných uzlů jako `string` nebo <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span><span class="sxs-lookup"><span data-stu-id="09621-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="09621-162">Následující metody třídy <xref:System.Xml.Schema.XmlSchemaValidator> přijímají jako parametr `delegate` <xref:System.Xml.Schema.XmlValueGetter>.</span><span class="sxs-lookup"><span data-stu-id="09621-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="09621-163">Následuje příklad <xref:System.Xml.Schema.XmlValueGetter>`delegate` z příkladu třídy <xref:System.Xml.Schema.XmlSchemaValidator> v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="09621-164"><xref:System.Xml.Schema.XmlValueGetter>`delegate` vrací hodnotu atributu jako objekt <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="09621-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="09621-165">Chcete-li ověřit, zda <xref:System.DateTime> objekt vrácený <xref:System.Xml.Schema.XmlValueGetter>, objekt <xref:System.Xml.Schema.XmlSchemaValidator> jej nejdříve převede na ValueType (ValueType je výchozí mapování CLR pro typ XSD) pro datový typ atributu a poté zkontroluje charakteristiky převedené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="09621-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

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

<span data-ttu-id="09621-166">Úplný příklad `delegate`<xref:System.Xml.Schema.XmlValueGetter>najdete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="09621-167">Další informace o <xref:System.Xml.Schema.XmlValueGetter>`delegate`naleznete v dokumentaci ke třídě <xref:System.Xml.Schema.XmlValueGetter>a <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="09621-168">Po ověření schématu – informace</span><span class="sxs-lookup"><span data-stu-id="09621-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="09621-169">Třída <xref:System.Xml.Schema.XmlSchemaInfo> představuje některé informace o uzlu XML, které jsou ověřeny třídou <xref:System.Xml.Schema.XmlSchemaValidator>, po ověření schématu.</span><span class="sxs-lookup"><span data-stu-id="09621-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="09621-170">Různé metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy přijímají <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako nepovinný parametr (`null`) `out`.</span><span class="sxs-lookup"><span data-stu-id="09621-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="09621-171">Po úspěšném ověření se vlastnosti objektu <xref:System.Xml.Schema.XmlSchemaInfo> nastaví s výsledky ověření.</span><span class="sxs-lookup"><span data-stu-id="09621-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="09621-172">Například po úspěšném ověření atributu pomocí metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> jsou vlastnosti objektu <xref:System.Xml.Schema.XmlSchemaInfo> (je-li zadán) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> vlastností nastaveny s výsledky ověření.</span><span class="sxs-lookup"><span data-stu-id="09621-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="09621-173">Následující metody třídy <xref:System.Xml.Schema.XmlSchemaValidator> přijímají <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="09621-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="09621-174">Úplný příklad třídy <xref:System.Xml.Schema.XmlSchemaInfo> naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="09621-175">Další informace o třídě <xref:System.Xml.Schema.XmlSchemaInfo> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaInfo>.</span><span class="sxs-lookup"><span data-stu-id="09621-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="09621-176">Načítání očekávaných částic, atributů a nespecifikovaných výchozích atributů</span><span class="sxs-lookup"><span data-stu-id="09621-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="09621-177">Třída <xref:System.Xml.Schema.XmlSchemaValidator> poskytuje metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> k načtení očekávaných částic, atributů a nespecifikovaných výchozích atributů v aktuálním kontextu ověřování.</span><span class="sxs-lookup"><span data-stu-id="09621-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="09621-178">Načítání očekávaných částic</span><span class="sxs-lookup"><span data-stu-id="09621-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="09621-179">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací pole <xref:System.Xml.Schema.XmlSchemaParticle> objektů, které obsahují očekávané částice v kontextu aktuálního prvku.</span><span class="sxs-lookup"><span data-stu-id="09621-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="09621-180">Platné částice, které mohou být vráceny metodou <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, jsou instance <xref:System.Xml.Schema.XmlSchemaElement> a třídy <xref:System.Xml.Schema.XmlSchemaAny>.</span><span class="sxs-lookup"><span data-stu-id="09621-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="09621-181">Když je kompozice pro model obsahu `xs:sequence`, vrátí se pouze další částice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="09621-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="09621-182">Pokud je kompozice pro model obsahu `xs:all` nebo `xs:choice`, budou vráceny všechny platné částice, které by mohly následovat v kontextu aktuálního prvku.</span><span class="sxs-lookup"><span data-stu-id="09621-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="09621-183">Pokud je metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> volána bezprostředně po volání metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí všechny globální prvky.</span><span class="sxs-lookup"><span data-stu-id="09621-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="09621-184">Například v schématu XML Schema Definition Language (XSD) a dokumentu XML, které následují, po ověření elementu `book` je prvek `book` aktuálním kontextem elementu.</span><span class="sxs-lookup"><span data-stu-id="09621-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="09621-185">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací pole obsahující jeden objekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentující prvek `title`.</span><span class="sxs-lookup"><span data-stu-id="09621-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="09621-186">Když je kontext ověření `title` element, metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="09621-187">Je-li metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> volána po ověření prvku `title`, ale před ověřením elementu `description`, vrátí pole obsahující jeden objekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentující `description` prvek.</span><span class="sxs-lookup"><span data-stu-id="09621-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="09621-188">Pokud je metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> volána po ověření prvku `description`, pak vrátí pole obsahující jeden objekt <xref:System.Xml.Schema.XmlSchemaAny> reprezentující zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="09621-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

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

 <span data-ttu-id="09621-189">Příklad má jako vstup následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="09621-189">The example takes the following XML as input:</span></span>

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

<span data-ttu-id="09621-190">Příklad má jako vstup následující schéma XSD:</span><span class="sxs-lookup"><span data-stu-id="09621-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="09621-191">Výsledky metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> jsou závislé na ověřeném aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="09621-192">Další informace najdete v části "kontext ověření" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="09621-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="09621-193">Příklad metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="09621-194">Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="09621-195">Načítání očekávaných atributů</span><span class="sxs-lookup"><span data-stu-id="09621-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="09621-196">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrací pole <xref:System.Xml.Schema.XmlSchemaAttribute> objektů, které obsahují očekávané atributy v kontextu aktuálního prvku.</span><span class="sxs-lookup"><span data-stu-id="09621-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="09621-197">Například v příkladu v úvodu je metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> použita k načtení všech atributů `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="09621-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="09621-198">Pokud zavoláte metodu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> hned po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metodě, vrátí se všechny atributy, které by mohly být zobrazeny v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="09621-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="09621-199">Nicméně pokud zavoláte metodu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> po jednom nebo více voláních metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, vrátí se atributy, které ještě nebyly ověřeny pro aktuální prvek.</span><span class="sxs-lookup"><span data-stu-id="09621-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="09621-200">Výsledky metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> jsou závislé na ověřeném aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="09621-201">Další informace najdete v části "kontext ověření" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="09621-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="09621-202">Příklad metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="09621-203">Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="09621-204">Načítání nespecifikovaných výchozích atributů</span><span class="sxs-lookup"><span data-stu-id="09621-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="09621-205">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> naplní <xref:System.Collections.ArrayList> zadané objekty <xref:System.Xml.Schema.XmlSchemaAttribute> pro všechny atributy výchozí hodnoty, které nebyly dříve ověřeny pomocí metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="09621-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="09621-206">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> by měla být volána po volání metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> v každém atributu v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="09621-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="09621-207">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> by měla být použita k určení, které výchozí atributy budou vloženy do ověřovaného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="09621-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="09621-208">Další informace o metodě <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="09621-209">Zpracování událostí ověřování schématu</span><span class="sxs-lookup"><span data-stu-id="09621-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="09621-210">Upozornění ověřování schématu a chyby zjištěné při ověřování jsou zpracovávány událostí <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="09621-211">Upozornění ověřování schématu mají <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu mají hodnotu <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="09621-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="09621-212">Pokud nebyla přiřazena žádná <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler>, je vyvolána <xref:System.Xml.Schema.XmlSchemaValidationException> pro všechny chyby ověřování schématu s hodnotou <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="09621-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="09621-213"><xref:System.Xml.Schema.XmlSchemaValidationException> však není vyvolána pro upozornění ověřování schématu s hodnotou <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="09621-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="09621-214">Následuje příklad <xref:System.Xml.Schema.ValidationEventHandler>, který přijímá upozornění ověřování schématu a chyby zjištěné při ověřování schématu provedené z příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

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

<span data-ttu-id="09621-215">Úplný příklad <xref:System.Xml.Schema.ValidationEventHandler>naleznete v příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="09621-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="09621-216">Další informace naleznete v referenční dokumentaci třídy <xref:System.Xml.Schema.XmlSchemaInfo>.</span><span class="sxs-lookup"><span data-stu-id="09621-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="09621-217">Přechod stavu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="09621-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="09621-218">Třída <xref:System.Xml.Schema.XmlSchemaValidator> má definovaný přechod stavu, který vynutila sekvenci a výskyt volání v každé z metod používaných k ověřování elementů, atributů a obsahu v XML informačním souboru.</span><span class="sxs-lookup"><span data-stu-id="09621-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="09621-219">Následující tabulka popisuje přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy a sekvenci a výskyt volání metody, které lze provést v každém stavu.</span><span class="sxs-lookup"><span data-stu-id="09621-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="09621-220">Stát</span><span class="sxs-lookup"><span data-stu-id="09621-220">State</span></span>|<span data-ttu-id="09621-221">Transition</span><span class="sxs-lookup"><span data-stu-id="09621-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="09621-222">Ověřit</span><span class="sxs-lookup"><span data-stu-id="09621-222">Validate</span></span>|<span data-ttu-id="09621-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; Toplevel \*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="09621-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="09621-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="09621-224">TopLevel</span></span>|<span data-ttu-id="09621-225">Element &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A></span><span class="sxs-lookup"><span data-stu-id="09621-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="09621-226">Prvek</span><span class="sxs-lookup"><span data-stu-id="09621-226">Element</span></span>|<span data-ttu-id="09621-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> obsahu\*)?</span><span class="sxs-lookup"><span data-stu-id="09621-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="09621-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="09621-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="09621-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="09621-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="09621-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> obsahu\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="09621-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="09621-231">Obsah</span><span class="sxs-lookup"><span data-stu-id="09621-231">Content</span></span>|<span data-ttu-id="09621-232">Element &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A></span><span class="sxs-lookup"><span data-stu-id="09621-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="09621-233"><xref:System.InvalidOperationException> je vyvolána každou metodou v tabulce výše, pokud je volání metody provedeno v nesprávné sekvenci podle aktuálního stavu objektu <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="09621-234">Výše uvedená tabulka přechodu stavu používá interpunkční znaménka k popisu metod a dalších stavů, které lze volat pro každý stav přechodu na stav <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="09621-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="09621-235">Použité symboly jsou stejné symboly, které najdete v referenčních standardech XML pro definici typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="09621-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="09621-236">Následující tabulka popisuje, jak se symboly interpunkčních znamének v tabulce přechodu stavu nacházejí výše ovlivňují metody a další stavy, které mohou být volány pro každý stav v přechodu stavu třídy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="09621-237">Symbol</span><span class="sxs-lookup"><span data-stu-id="09621-237">Symbol</span></span>|<span data-ttu-id="09621-238">Popis</span><span class="sxs-lookup"><span data-stu-id="09621-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="09621-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="09621-239">&#124;</span></span>|<span data-ttu-id="09621-240">Lze zavolat buď metodu, nebo stav (jeden před pruhový nebo ten).</span><span class="sxs-lookup"><span data-stu-id="09621-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="09621-241">?</span><span class="sxs-lookup"><span data-stu-id="09621-241">?</span></span>|<span data-ttu-id="09621-242">Metoda nebo stav, který předchází otazník je volitelný, ale pokud je volána, lze ji volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="09621-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|*|<span data-ttu-id="09621-243">Metoda nebo stav, který předchází symbolu \* je volitelná a může být volána více než jednou.</span><span class="sxs-lookup"><span data-stu-id="09621-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="09621-244">Kontext ověřování</span><span class="sxs-lookup"><span data-stu-id="09621-244">Validation Context</span></span>

<span data-ttu-id="09621-245">Metody třídy <xref:System.Xml.Schema.XmlSchemaValidator> používané k ověřování elementů, atributů a obsahu v XML informačním souboru, mění kontext ověření objektu <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="09621-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="09621-246">Například metoda <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> přeskočí ověřování aktuálního obsahu prvku a připraví objekt <xref:System.Xml.Schema.XmlSchemaValidator> k ověření obsahu v kontextu nadřazeného elementu; je ekvivalentní k přeskočení ověřování pro všechny podřízené položky aktuálního prvku a následnému volání metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="09621-247">Výsledky metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> třídy <xref:System.Xml.Schema.XmlSchemaValidator> jsou závislé na ověřeném aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="09621-248">Následující tabulka popisuje výsledky volání těchto metod po volání jedné z metod <xref:System.Xml.Schema.XmlSchemaValidator> třídy používané pro ověřování prvků, atributů a obsahu v XML informačním souboru.</span><span class="sxs-lookup"><span data-stu-id="09621-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="09621-249">Metoda</span><span class="sxs-lookup"><span data-stu-id="09621-249">Method</span></span>|<span data-ttu-id="09621-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="09621-250">GetExpectedParticles</span></span>|<span data-ttu-id="09621-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="09621-251">GetExpectedAttributes</span></span>|<span data-ttu-id="09621-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="09621-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="09621-253">Pokud je volána výchozí metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pole obsahující všechny globální prvky.</span><span class="sxs-lookup"><span data-stu-id="09621-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="09621-254">Pokud je pro inicializaci částečného ověřování prvku volána přetížená <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému byl objekt <xref:System.Xml.Schema.XmlSchemaValidator> inicializován.</span><span class="sxs-lookup"><span data-stu-id="09621-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="09621-255">Pokud je volána výchozí metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="09621-256">Pokud je volání metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, pro inicializaci částečného ověřování atributu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut, pro který byl objekt <xref:System.Xml.Schema.XmlSchemaValidator> inicializován.</span><span class="sxs-lookup"><span data-stu-id="09621-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="09621-257">Přidá schéma do <xref:System.Xml.Schema.XmlSchemaSet> objektu <xref:System.Xml.Schema.XmlSchemaValidator>, pokud neobsahuje žádné chyby předzpracování.</span><span class="sxs-lookup"><span data-stu-id="09621-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="09621-258">Je-li prvek kontextu platný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávaných jako podřízené objekty kontextu prvku.</span><span class="sxs-lookup"><span data-stu-id="09621-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="09621-259">Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="09621-260">Pokud je kontextový prvek platný a pokud předtím nebylo provedeno žádné volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam všech atributů definovaných v prvku Context.</span><span class="sxs-lookup"><span data-stu-id="09621-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="09621-261">Pokud některé atributy již byly ověřeny, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývajících atributů, které mají být ověřeny.</span><span class="sxs-lookup"><span data-stu-id="09621-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="09621-262">Pokud je prvek kontextu neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="09621-263">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="09621-264">Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="09621-265">Jinak <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávanou jako první podřízený prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="09621-266">Pokud je atributem kontextu atribut nejvyšší úrovně, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="09621-267">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývajících atributů, které mají být ověřeny.</span><span class="sxs-lookup"><span data-stu-id="09621-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="09621-268">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="09621-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="09621-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam požadovaných a volitelných atributů, které se ještě ověřují pro prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="09621-271">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="09621-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací sekvenci prvků očekávanou jako první podřízený prvek kontextu.</span><span class="sxs-lookup"><span data-stu-id="09621-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="09621-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="09621-274">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="09621-275">Pokud je třída contentType elementu kontextu smíšená, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávanou v další pozici.</span><span class="sxs-lookup"><span data-stu-id="09621-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="09621-276">Pokud je třída contentType elementu kontextu typu TextOnly nebo prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="09621-277">Pokud je objekt contentType elementu kontextu ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekávanou na další pozici, ale k chybě ověřování již došlo.</span><span class="sxs-lookup"><span data-stu-id="09621-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="09621-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam atributů kontextového prvku, který není ověřený.</span><span class="sxs-lookup"><span data-stu-id="09621-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="09621-279">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="09621-280">Pokud je místo v kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="09621-281">V opačném případě je chování metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="09621-282">Pokud je místo v kontextu prázdné místo na nejvyšší úrovni, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="09621-283">V opačném případě je chování metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="09621-284">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="09621-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrací sekvenci prvků očekávaných po elementu kontextu (možné na stejné úrovni).</span><span class="sxs-lookup"><span data-stu-id="09621-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="09621-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam atributů kontextového prvku, který není ověřený.</span><span class="sxs-lookup"><span data-stu-id="09621-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="09621-287">Pokud kontextový prvek nemá žádnou nadřazenou položku, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdný seznam (kontextový prvek je nadřazeným prvkem aktuálního prvku, na kterém <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> byla volána).</span><span class="sxs-lookup"><span data-stu-id="09621-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="09621-288">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="09621-289">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="09621-290">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="09621-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="09621-291">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="09621-292">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-292">Returns an empty array.</span></span>|<span data-ttu-id="09621-293">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="09621-293">Returns an empty array.</span></span>|<span data-ttu-id="09621-294">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="09621-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="09621-295">Hodnoty vrácené různými vlastnostmi <xref:System.Xml.Schema.XmlSchemaValidator> třídy nejsou změněny voláním libovolné metody ve výše uvedené tabulce.</span><span class="sxs-lookup"><span data-stu-id="09621-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="09621-296">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09621-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
