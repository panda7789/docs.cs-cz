---
title: Nabízené ověření XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d1d5602ff224c1c8f3e0948fc93c9200b9661e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189073"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="4c685-102">Nabízené ověření XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="4c685-102">XmlSchemaValidator Push-Based Validation</span></span>
<span data-ttu-id="4c685-103"><xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje mechanismus efektivního, vysoce výkonné ověřit data XML oproti schémat XML v podobě nabízené.</span><span class="sxs-lookup"><span data-stu-id="4c685-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="4c685-104">Například <xref:System.Xml.Schema.XmlSchemaValidator> třída umožňuje ověřit XML informační sadu místní bez nutnosti ho serializovat jako dokument XML a potom změny zpracování dokumentu pomocí ověřování čtecí modul XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>  
  
 <span data-ttu-id="4c685-105"><xref:System.Xml.Schema.XmlSchemaValidator> Třída může být použita v pokročilých scénářích, jako je například vytváření modulů ověřování přes vlastní zdroje dat XML nebo jako způsob, jak sestavit ověřování zapisovače XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>  
  
 <span data-ttu-id="4c685-106">Následuje příklad použití <xref:System.Xml.Schema.XmlSchemaValidator> třídy k ověření `contosoBooks.xml` souboru proti `contosoBooks.xsd` schématu.</span><span class="sxs-lookup"><span data-stu-id="4c685-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="4c685-107">V příkladu se používá <xref:System.Xml.Serialization.XmlSerializer> třídy k deserializaci `contosoBooks.xml` souboru a předat hodnotu uzly do metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c685-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c685-108">V tomto příkladu se používají v částech tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4c685-108">This example is used throughout the sections of this topic.</span></span>  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 <span data-ttu-id="4c685-109">V příkladu přebírá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4c685-109">The example takes the `contosoBooks.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4c685-110">Tento příklad využívá taky `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4c685-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
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
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="4c685-111">Ověřování dat XML pomocí XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="4c685-111">Validating XML Data using XmlSchemaValidator</span></span>  
 <span data-ttu-id="4c685-112">Pokud chcete začít, ověřování informační sadu XML, musí nejprve inicializovat novou instanci třídy <xref:System.Xml.Schema.XmlSchemaValidator> pomocí <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4c685-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>  
  
 <span data-ttu-id="4c685-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Přebírá konstruktor <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, a <xref:System.Xml.XmlNamespaceManager> objektů jako parametry a také <xref:System.Xml.Schema.XmlSchemaValidationFlags> hodnotu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4c685-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="4c685-114"><xref:System.Xml.XmlNameTable> Objektu se používá k atomizovat dobře známé obor názvů řetězce jako obor názvů schématu, obor názvů XML a tak dále a je předán <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metoda při ověřování jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="4c685-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="4c685-115"><xref:System.Xml.Schema.XmlSchemaSet> Objekt obsahuje schémata XML používaná k ověření informační sadu XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="4c685-116"><xref:System.Xml.XmlNamespaceManager> Objektu se používá k překladu názvů při ověřování došlo k.</span><span class="sxs-lookup"><span data-stu-id="4c685-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="4c685-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags> Hodnota slouží k zakázání určitých funkcí ověření.</span><span class="sxs-lookup"><span data-stu-id="4c685-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>  
  
 <span data-ttu-id="4c685-118">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="initializing-validation"></a><span data-ttu-id="4c685-119">Inicializuje se ověření</span><span class="sxs-lookup"><span data-stu-id="4c685-119">Initializing Validation</span></span>  
 <span data-ttu-id="4c685-120">Po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen, existují dvě přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody použité k inicializaci stav <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="4c685-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="4c685-121">Tady jsou dva <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4c685-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="4c685-122">Výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu na jeho počáteční stav a přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu počáteční stav pro částečné ověření.</span><span class="sxs-lookup"><span data-stu-id="4c685-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="4c685-123">Obě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody lze volat pouze ihned po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen nebo po volání <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c685-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>  
  
 <span data-ttu-id="4c685-124">Příklad <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metodou, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="4c685-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="4c685-125">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="partial-validation"></a><span data-ttu-id="4c685-126">Částečné ověřování</span><span class="sxs-lookup"><span data-stu-id="4c685-126">Partial Validation</span></span>  
 <span data-ttu-id="4c685-127"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu počáteční stav pro částečné ověřování.</span><span class="sxs-lookup"><span data-stu-id="4c685-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="4c685-128">V následujícím příkladu <xref:System.Xml.Schema.XmlSchemaObject> je inicializován pro částečné ověřování pomocí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4c685-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4c685-129">`orderNumber` Element schématu je předán tak, že vyberete element schématu pomocí <xref:System.Xml.XmlQualifiedName> v <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekci vrácené poskytovatelem <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> objektu.</span><span class="sxs-lookup"><span data-stu-id="4c685-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="4c685-130"><xref:System.Xml.Schema.XmlSchemaValidator> Objekt pak ověří tato konkrétní elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>  
  
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
  
 <span data-ttu-id="4c685-131">Příklad vezme jako vstupní údaje následujícího schématu XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-131">The example takes the following XML schema as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="4c685-132">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="adding-additional-schemas"></a><span data-ttu-id="4c685-133">Přidat další schémata</span><span class="sxs-lookup"><span data-stu-id="4c685-133">Adding Additional Schemas</span></span>  
 <span data-ttu-id="4c685-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metodu <xref:System.Xml.Schema.XmlSchemaValidator> třída se používá k přidání schématu XML na sadu při ověřování se používají schémata.</span><span class="sxs-lookup"><span data-stu-id="4c685-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="4c685-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda umožňuje simulovat účinek zjištění vložené schéma XML v informační sadu XML, které se ověřují.</span><span class="sxs-lookup"><span data-stu-id="4c685-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c685-136">Cílový obor názvů <xref:System.Xml.Schema.XmlSchema> parametr se nemůže shodovat, který všechny elementu nebo atributu už, se kterými <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="4c685-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
>   
>  <span data-ttu-id="4c685-137">Pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> hodnotu nebyl předán jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda nemá žádný účinek.</span><span class="sxs-lookup"><span data-stu-id="4c685-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>  
  
 <span data-ttu-id="4c685-138">Výsledkem <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda je závislé na aktuálním kontextu uzlu XML ověřován.</span><span class="sxs-lookup"><span data-stu-id="4c685-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="4c685-139">Další informace o ověření kontextů najdete v části "Ověření kontextu" tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4c685-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="4c685-140">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="4c685-141">Ověřování elementů, atributů a obsahu</span><span class="sxs-lookup"><span data-stu-id="4c685-141">Validating Elements, Attributes, and Content</span></span>  
 <span data-ttu-id="4c685-142"><xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje několik metod, které slouží k ověření elementů, atributů a obsahu v informační sadu XML pomocí schémat XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="4c685-143">Následující tabulka popisuje každý z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="4c685-143">The following table describes each of these methods.</span></span>  
  
|<span data-ttu-id="4c685-144">Metoda</span><span class="sxs-lookup"><span data-stu-id="4c685-144">Method</span></span>|<span data-ttu-id="4c685-145">Popis</span><span class="sxs-lookup"><span data-stu-id="4c685-145">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="4c685-146">Ověří název elementu v aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="4c685-146">Validates the element name in the current context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="4c685-147">Ověří atributů v rámci aktuálního kontextu elementu nebo proti <xref:System.Xml.Schema.XmlSchemaAttribute> objekt předán jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4c685-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="4c685-148">Ověří, zda všechny povinné atributy v kontextu elementu jsou k dispozici a připraví <xref:System.Xml.Schema.XmlSchemaValidator> pro ověření podřízený obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="4c685-149">Ověřuje, zda je povolen v rámci aktuálního kontextu elementu textu a shromažďuje text pro ověření, pokud je aktuální prvek má jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="4c685-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="4c685-150">Ověřuje, zda je prázdné místo je povolen v rámci aktuálního kontextu elementu a shromažďuje mezer pro ověření, zda aktuální prvek má jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="4c685-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="4c685-151">Ověří, zda textový obsah elementu, který je platný podle jeho datového typu pro prvky s jednoduchým obsahem a ověří, zda je obsah aktuální prvek kompletní pro elementy se složitým obsahem.</span><span class="sxs-lookup"><span data-stu-id="4c685-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="4c685-152">Přeskočí ověření aktuální obsah elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objektu na ověřování obsahu v rámci nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="4c685-153">Ukončí ověření a zkontroluje omezení identity pro celý dokument XML, pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> je nastavena možnost ověřování.</span><span class="sxs-lookup"><span data-stu-id="4c685-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4c685-154"><xref:System.Xml.Schema.XmlSchemaValidator> Třída má definovaný stavu přechodu, který vynucuje pořadí a výskyt volání na každý z metod popsaných v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="4c685-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="4c685-155">Přechod určitý stav <xref:System.Xml.Schema.XmlSchemaValidator> třídy je popsaný v části "XmlSchemaValidator přechod stavu" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4c685-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>  
  
 <span data-ttu-id="4c685-156">Příklad metody použité k ověření elementů, atributů a obsahu v informační sadu XML podívejte se na příklad v předchozím oddílu.</span><span class="sxs-lookup"><span data-stu-id="4c685-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="4c685-157">Další informace o těchto metodách v tématu <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="4c685-158">Ověřování obsahu pomocí XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="4c685-158">Validating Content Using an XmlValueGetter</span></span>  
 <span data-ttu-id="4c685-159"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Je možné předat hodnotu atributu, text nebo prázdný znak uzlů jako typy Common Language Runtime (CLR) kompatibilní s typem jazyka pro definici schématu XML (XSD) atribut, text nebo uzel prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="4c685-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="4c685-160"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Je užitečné, pokud CLR hodnotu atributu, text nebo uzel prázdné místo je již k dispozici a zabraňuje převodu na náklady `string` a pak ho znovu reparsing pro ověření.</span><span class="sxs-lookup"><span data-stu-id="4c685-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>  
  
 <span data-ttu-id="4c685-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, A <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> metody jsou přetížené a přijmout hodnotu atributu, text nebo prázdný znak uzlů jako `string` nebo <xref:System.Xml.Schema.XmlValueGetter> `delegate`.</span><span class="sxs-lookup"><span data-stu-id="4c685-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>  
  
 <span data-ttu-id="4c685-162">Tyto metody <xref:System.Xml.Schema.XmlSchemaValidator> přijmout třídy <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4c685-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 <span data-ttu-id="4c685-163">Tady je příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate` z <xref:System.Xml.Schema.XmlSchemaValidator> úvodním příkladem třídu.</span><span class="sxs-lookup"><span data-stu-id="4c685-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="4c685-164"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Vrátí hodnotu jako atribut <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="4c685-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="4c685-165">Chcete-li to ověřit <xref:System.DateTime> objekt vrácený <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> objekt nejprve převeden na typ hodnoty (ValueType je výchozí mapování modulu CLR pro typ XSD) pro datový typ atributu a kontroly omezující vlastnosti na převedenou hodnotu hodnota.</span><span class="sxs-lookup"><span data-stu-id="4c685-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>  
  
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
  
 <span data-ttu-id="4c685-166">Kompletní příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate`, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="4c685-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="4c685-167">Další informace o <xref:System.Xml.Schema.XmlValueGetter> `delegate`, najdete v článku <xref:System.Xml.Schema.XmlValueGetter>, a <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="post-schema-validation-information"></a><span data-ttu-id="4c685-168">Po-Schema--informace o ověřování</span><span class="sxs-lookup"><span data-stu-id="4c685-168">Post-Schema-Validation-Information</span></span>  
 <span data-ttu-id="4c685-169"><xref:System.Xml.Schema.XmlSchemaInfo> Třída představuje některé po-Schema-ověření – informace o uzlu XML ověřen <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c685-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="4c685-170">Různé metody <xref:System.Xml.Schema.XmlSchemaValidator> přijmout třídy <xref:System.Xml.Schema.XmlSchemaInfo> objektu jako volitelný, (`null`) `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="4c685-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>  
  
 <span data-ttu-id="4c685-171">Po úspěšném ověření, vlastnosti <xref:System.Xml.Schema.XmlSchemaInfo> objektu se nastavují s výsledky ověření.</span><span class="sxs-lookup"><span data-stu-id="4c685-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="4c685-172">Například po úspěšném ověření pomocí atributu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> objektu uživatele (Pokud je zadaný) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> s výsledky ověření jsou nastaveny vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="4c685-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>  
  
 <span data-ttu-id="4c685-173">Následující <xref:System.Xml.Schema.XmlSchemaValidator> přijmout metody třídy <xref:System.Xml.Schema.XmlSchemaInfo> objekt jako výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="4c685-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 <span data-ttu-id="4c685-174">Kompletní příklad <xref:System.Xml.Schema.XmlSchemaInfo> třídy, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="4c685-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="4c685-175">Další informace o <xref:System.Xml.Schema.XmlSchemaInfo> najdete v tématu <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="4c685-176">Načítání očekávané částice, atributy a neurčené výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="4c685-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>  
 <span data-ttu-id="4c685-177"><xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody pro načtení očekávané částice, atributy a neurčené výchozí atributy v aktuálním kontextu ověřování.</span><span class="sxs-lookup"><span data-stu-id="4c685-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>  
  
#### <a name="retrieving-expected-particles"></a><span data-ttu-id="4c685-178">Načítání očekávané částice</span><span class="sxs-lookup"><span data-stu-id="4c685-178">Retrieving Expected Particles</span></span>  
 <span data-ttu-id="4c685-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaParticle> objekty, které obsahují očekávané částice v rámci aktuálního kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="4c685-180">Platný částice, které může být vrácen <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody jsou instance <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAny> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c685-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>  
  
 <span data-ttu-id="4c685-181">Když složku pro obsahový model je `xs:sequence`, je vrácen pouze další částice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4c685-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="4c685-182">Pokud je složku pro model obsahu `xs:all` nebo `xs:choice`, pak jsou vráceny všechny platné částice, které byste mohli provést, v rámci aktuálního kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c685-183">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána ihned po volání <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí všechny globální prvky.</span><span class="sxs-lookup"><span data-stu-id="4c685-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>  
  
 <span data-ttu-id="4c685-184">Například v schématu XML definice jazyk (XSD) schématu a XML dokumentů, které následují po ověření `book` elementu, `book` element je aktuálního kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="4c685-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt představující `title` elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="4c685-186">Pokud je kontext ověřování `title` elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="4c685-187">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `title` element ověřily ale předtím, než `description` element byl ověřen, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt představující `description` elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="4c685-188">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `description` element byl ověřen a vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaAny> objekt představující zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="4c685-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>  
  
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
  
 <span data-ttu-id="4c685-189">Příklad vezme jako vstupní údaje následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-189">The example takes the following XML as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="4c685-190">Příklad vezme jako vstupní údaje následující schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="4c685-190">The example takes the following XSD schema as input.</span></span>  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  <span data-ttu-id="4c685-191">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídě jsou závislé na aktuálním kontextu se ověřují.</span><span class="sxs-lookup"><span data-stu-id="4c685-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="4c685-192">Další informace najdete v části "Ověření kontextu" tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4c685-192">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="4c685-193">Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodou, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="4c685-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="4c685-194">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="4c685-195">Načítání očekávané atributy</span><span class="sxs-lookup"><span data-stu-id="4c685-195">Retrieving Expected Attributes</span></span>  
 <span data-ttu-id="4c685-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaAttribute> objekty, které obsahují očekávané atributy v rámci aktuálního kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>  
  
 <span data-ttu-id="4c685-197">Například v příkladu v úvodu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda se používá k načtení všech atributů `book` element.</span><span class="sxs-lookup"><span data-stu-id="4c685-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>  
  
 <span data-ttu-id="4c685-198">Při volání <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda ihned po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metody, jsou vráceny všechny atributy, které mohou být zobrazeny v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="4c685-199">Ale při volání <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> za jeden nebo více volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody, jsou vráceny atributy, které ještě neověřily aktuálního elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c685-200">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídě jsou závislé na aktuálním kontextu se ověřují.</span><span class="sxs-lookup"><span data-stu-id="4c685-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="4c685-201">Další informace najdete v části "Ověření kontextu" tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4c685-201">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="4c685-202">Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodou, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="4c685-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="4c685-203">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="4c685-204">Načítání neurčené výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="4c685-204">Retrieving Unspecified Default Attributes</span></span>  
 <span data-ttu-id="4c685-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda naplní <xref:System.Collections.ArrayList> zadaným <xref:System.Xml.Schema.XmlSchemaAttribute> objekty pro atributy s výchozími hodnotami, které nebyly ověřené dříve pomocí <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="4c685-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla být volána po volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metodu na jednotlivé atributy v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="4c685-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla sloužit k určení výchozí atributy jsou má být vložen do dokumentu XML, který je ověřován.</span><span class="sxs-lookup"><span data-stu-id="4c685-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>  
  
 <span data-ttu-id="4c685-208">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="handling-schema-validation-events"></a><span data-ttu-id="4c685-209">Zpracování událostí ověření schématu</span><span class="sxs-lookup"><span data-stu-id="4c685-209">Handling Schema Validation Events</span></span>  
 <span data-ttu-id="4c685-210">Schéma ověření upozornění a chyb zjištěných při ověřování jsou zpracovávány <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> událost <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c685-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
 <span data-ttu-id="4c685-211">Schéma ověření upozornění mají <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="4c685-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="4c685-212">Pokud ne <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> byla přiřazena, <xref:System.Xml.Schema.XmlSchemaValidationException> všechny chyby ověřování schématu s, je vyvolána <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="4c685-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="4c685-213">Však <xref:System.Xml.Schema.XmlSchemaValidationException> není vyvolána pro upozornění při ověřování schématu s <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="4c685-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>  
  
 <span data-ttu-id="4c685-214">Následující je příklad <xref:System.Xml.Schema.ValidationEventHandler> , která obdrží upozornění při ověřování schématu a chyb při ověřování schématu z úvodním příkladem.</span><span class="sxs-lookup"><span data-stu-id="4c685-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>  
  
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
  
 <span data-ttu-id="4c685-215">Kompletní příklad <xref:System.Xml.Schema.ValidationEventHandler>, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="4c685-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="4c685-216">Další informace najdete v tématu <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4c685-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="4c685-217">Přechod stavu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="4c685-217">XmlSchemaValidator State Transition</span></span>  
 <span data-ttu-id="4c685-218"><xref:System.Xml.Schema.XmlSchemaValidator> Třída má definovaný stavu přechodu, který vynucuje pořadí a výskyt volání na jednotlivé metody použité k ověření elementů, atributů a obsahu v informační sadu XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
 <span data-ttu-id="4c685-219">Následující tabulka popisuje přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy a pořadí a výskyt volání metody, které mohou být provedeny v jednotlivých stavech.</span><span class="sxs-lookup"><span data-stu-id="4c685-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>  
  
|<span data-ttu-id="4c685-220">Stav</span><span class="sxs-lookup"><span data-stu-id="4c685-220">State</span></span>|<span data-ttu-id="4c685-221">Přechod</span><span class="sxs-lookup"><span data-stu-id="4c685-221">Transition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="4c685-222">Ověření</span><span class="sxs-lookup"><span data-stu-id="4c685-222">Validate</span></span>|<span data-ttu-id="4c685-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel \*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="4c685-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|  
|<span data-ttu-id="4c685-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="4c685-224">TopLevel</span></span>|<span data-ttu-id="4c685-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; – Element</span><span class="sxs-lookup"><span data-stu-id="4c685-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
|<span data-ttu-id="4c685-226">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c685-226">Element</span></span>|<span data-ttu-id="4c685-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\*)?</span><span class="sxs-lookup"><span data-stu-id="4c685-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="4c685-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="4c685-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="4c685-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="4c685-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="4c685-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="4c685-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|  
|<span data-ttu-id="4c685-231">Obsah</span><span class="sxs-lookup"><span data-stu-id="4c685-231">Content</span></span>|<span data-ttu-id="4c685-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; – Element</span><span class="sxs-lookup"><span data-stu-id="4c685-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4c685-233"><xref:System.InvalidOperationException> Je vyvolána každou z metod uvedených v tabulce výše, při volání metody se provádí v nesprávné pořadí podle aktuálního stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="4c685-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
  
 <span data-ttu-id="4c685-234">Výše uvedené tabulce přechodu stavu pomocí interpunkčních znamének jsou popsány metody a ostatní stavy, které lze volat pro každý stav přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c685-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="4c685-235">Symboly použité jsou stejné symboly součástí reference na standardy XML pro definici typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="4c685-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>  
  
 <span data-ttu-id="4c685-236">Následující tabulka popisuje vlivu metody interpunkčních znamének v předchozí tabulce přechod stavu a ostatní stavy, které lze volat pro každý stav ve stavu přechodu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c685-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
|<span data-ttu-id="4c685-237">Symbol</span><span class="sxs-lookup"><span data-stu-id="4c685-237">Symbol</span></span>|<span data-ttu-id="4c685-238">Popis</span><span class="sxs-lookup"><span data-stu-id="4c685-238">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4c685-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="4c685-239">&#124;</span></span>|<span data-ttu-id="4c685-240">Je možné volat metodu nebo stavu (jeden před panelu) nebo jedna po ní.</span><span class="sxs-lookup"><span data-stu-id="4c685-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|  
|<span data-ttu-id="4c685-241">?</span><span class="sxs-lookup"><span data-stu-id="4c685-241">?</span></span>|<span data-ttu-id="4c685-242">Metoda a stav, který předchází otazník je volitelný, ale pokud je volána jej lze volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="4c685-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|  
|*|<span data-ttu-id="4c685-243">Metoda nebo stav, který předchází \* symbol je volitelný a může být volána více než jednou.</span><span class="sxs-lookup"><span data-stu-id="4c685-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|  
  
## <a name="validation-context"></a><span data-ttu-id="4c685-244">Kontext ověřování</span><span class="sxs-lookup"><span data-stu-id="4c685-244">Validation Context</span></span>  
 <span data-ttu-id="4c685-245">Metody <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření elementů, atributů a obsahu v informační sadu XML, změňte kontext ověřování ze <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="4c685-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="4c685-246">Například <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> metoda přeskočí ověření aktuální obsah elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objektu na ověřování obsahu v rámci nadřazeného elementu; je ekvivalentní k přeskočení ověření pro všechny podřízené objekty aktuálního elementu a následným voláním <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4c685-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>  
  
 <span data-ttu-id="4c685-247">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídě jsou závislé na aktuálním kontextu se ověřují.</span><span class="sxs-lookup"><span data-stu-id="4c685-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>  
  
 <span data-ttu-id="4c685-248">Následující tabulka popisuje výsledky volání těchto metod po volání jedné z metod <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření elementů, atributů a obsahu v informační sadu XML.</span><span class="sxs-lookup"><span data-stu-id="4c685-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
|<span data-ttu-id="4c685-249">Metoda</span><span class="sxs-lookup"><span data-stu-id="4c685-249">Method</span></span>|<span data-ttu-id="4c685-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="4c685-250">GetExpectedParticles</span></span>|<span data-ttu-id="4c685-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="4c685-251">GetExpectedAttributes</span></span>|<span data-ttu-id="4c685-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="4c685-252">AddSchema</span></span>|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="4c685-253">Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pole obsahující všechny globální prvky.</span><span class="sxs-lookup"><span data-stu-id="4c685-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="4c685-254">Pokud přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr je volána k inicializaci částečné ověřování elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="4c685-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="4c685-255">Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="4c685-256">Pokud přetížení <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, která přebírá <xref:System.Xml.Schema.XmlSchemaObject> jako parametr je volána k inicializaci částečné ověřování atributu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut ke kterému <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="4c685-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="4c685-257">Přidá schématu tak <xref:System.Xml.Schema.XmlSchemaSet> z <xref:System.Xml.Schema.XmlSchemaValidator> objektu, pokud ho neobsahuje žádné chyby během předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="4c685-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="4c685-258">Pokud je platný, element kontextu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekáván jako podřízené položky elementu kontextu.</span><span class="sxs-lookup"><span data-stu-id="4c685-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="4c685-259">Pokud není platný, element kontextu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="4c685-260">Pokud element kontextu je platný a pokud bez volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> bylo dříve vytvořeno <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam všech atributů definovaných v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="4c685-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="4c685-261">Pokud některé atributy již byly ověřeny, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam hodnot zbývajících atributy, které mají být ověřen.</span><span class="sxs-lookup"><span data-stu-id="4c685-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="4c685-262">Pokud není platný, element kontextu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="4c685-263">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-263">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="4c685-264">Pokud atribut kontextu je atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="4c685-265">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekává jako první podřízený element kontextu.</span><span class="sxs-lookup"><span data-stu-id="4c685-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="4c685-266">Pokud atribut kontextu je atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="4c685-267">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývající atributů má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="4c685-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="4c685-268">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-268">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="4c685-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí sekvenci prvků očekává jako první podřízený element kontextu.</span><span class="sxs-lookup"><span data-stu-id="4c685-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="4c685-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí seznam povinných a volitelných atributů, které se ještě na ověření pro element kontextu.</span><span class="sxs-lookup"><span data-stu-id="4c685-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="4c685-271">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-271">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="4c685-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí sekvenci prvků očekává jako první podřízený element kontextu.</span><span class="sxs-lookup"><span data-stu-id="4c685-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="4c685-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="4c685-274">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-274">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="4c685-275">Pokud element kontextu contentType je kombinovat, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekává na další pozici.</span><span class="sxs-lookup"><span data-stu-id="4c685-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="4c685-276">Pokud element kontextu contentType je typu TextOnly nebo je prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="4c685-277">Pokud element kontextu contentType je ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí sekvenci prvků očekáván na další pozici, ale k chybě ověřování již došlo.</span><span class="sxs-lookup"><span data-stu-id="4c685-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="4c685-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí element kontextu seznam atributů nebyl ověřen.</span><span class="sxs-lookup"><span data-stu-id="4c685-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="4c685-279">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-279">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="4c685-280">Pokud prázdnému kontextu je nejvyšší úrovně prázdných <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="4c685-281">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c685-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="4c685-282">Pokud prázdnému kontextu je nejvyšší úrovně prázdných <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="4c685-283">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c685-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="4c685-284">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-284">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="4c685-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí sekvenci prvků po elementu kontextu (je to možné na stejné úrovni).</span><span class="sxs-lookup"><span data-stu-id="4c685-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="4c685-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí element kontextu seznam atributů nebyl ověřen.</span><span class="sxs-lookup"><span data-stu-id="4c685-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="4c685-287">Pokud element kontextu nemá žádný nadřazený objekt pak <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdný seznam (element kontextu je nadřazeného člena aktuální prvek, na který <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> byla volána).</span><span class="sxs-lookup"><span data-stu-id="4c685-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="4c685-288">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-288">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="4c685-289">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c685-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="4c685-290">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c685-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="4c685-291">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-291">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="4c685-292">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-292">Returns an empty array.</span></span>|<span data-ttu-id="4c685-293">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="4c685-293">Returns an empty array.</span></span>|<span data-ttu-id="4c685-294">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="4c685-294">Same as above.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4c685-295">Hodnoty vrácené různé vlastnosti objektu <xref:System.Xml.Schema.XmlSchemaValidator> třídy se nezmění voláním některé z metod ve výše uvedené tabulky.</span><span class="sxs-lookup"><span data-stu-id="4c685-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c685-296">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c685-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
