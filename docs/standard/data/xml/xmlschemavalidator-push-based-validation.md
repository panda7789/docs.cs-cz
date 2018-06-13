---
title: Ověření nabízené XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 36d91d4bd479c1592ae0b3f98d227947686188d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579597"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="f37ed-102">Ověření nabízené XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="f37ed-102">XmlSchemaValidator Push-Based Validation</span></span>
<span data-ttu-id="f37ed-103"><xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje mechanismus efektivní, vysoce výkonných ověřit data XML oproti schémat XML způsobem nabízené.</span><span class="sxs-lookup"><span data-stu-id="f37ed-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="f37ed-104">Například <xref:System.Xml.Schema.XmlSchemaValidator> třída umožňuje ověřit XML informační sadu místní bez nutnosti serializovat jako dokument XML a pak rozboru dokument pomocí ověřování čtečky XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>  
  
 <span data-ttu-id="f37ed-105"><xref:System.Xml.Schema.XmlSchemaValidator> Třídu lze použít v pokročilých scénářích, jako je například vytváření modulů ověření přes vlastní zdroje dat XML nebo jako způsob, jak sestavit ověřování zapisovače XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>  
  
 <span data-ttu-id="f37ed-106">Následuje příklad použití <xref:System.Xml.Schema.XmlSchemaValidator> třída k ověření `contosoBooks.xml` souboru proti `contosoBooks.xsd` schématu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="f37ed-107">V příkladu se používá <xref:System.Xml.Serialization.XmlSerializer> třída k deserializaci `contosoBooks.xml` souborů a předat hodnotu uzlů do metody <xref:System.Xml.Schema.XmlSchemaValidator> – třída.</span><span class="sxs-lookup"><span data-stu-id="f37ed-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-108">V tomto příkladu se používá napříč částech tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-108">This example is used throughout the sections of this topic.</span></span>  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 <span data-ttu-id="f37ed-109">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f37ed-109">The example takes the `contosoBooks.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f37ed-110">Tento příklad také trvá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f37ed-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
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
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="f37ed-111">Ověřování pomocí XmlSchemaValidator dat XML</span><span class="sxs-lookup"><span data-stu-id="f37ed-111">Validating XML Data using XmlSchemaValidator</span></span>  
 <span data-ttu-id="f37ed-112">Pokud chcete začít, ověřování informační sadu XML, musí nejprve inicializovat novou instanci třídy <xref:System.Xml.Schema.XmlSchemaValidator> pomocí <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f37ed-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>  
  
 <span data-ttu-id="f37ed-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Konstruktor přijímá <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, a <xref:System.Xml.XmlNamespaceManager> objektů jako parametry a také <xref:System.Xml.Schema.XmlSchemaValidationFlags> hodnotu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f37ed-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="f37ed-114"><xref:System.Xml.XmlNameTable> Objekt se používá k atomizovat dobře známé obor názvů řetězce jako obor názvů schématu, obor názvů XML a tak dále a je předána <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metoda při ověřování jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="f37ed-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="f37ed-115"><xref:System.Xml.Schema.XmlSchemaSet> Objekt obsahuje schémat XML použitý k ověření informační sadu XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="f37ed-116"><xref:System.Xml.XmlNamespaceManager> Objekt se používá k překladu při ověřování došlo k obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f37ed-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="f37ed-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags> Hodnota se používá k zakázání určitých funkcí ověření.</span><span class="sxs-lookup"><span data-stu-id="f37ed-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>  
  
 <span data-ttu-id="f37ed-118">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="initializing-validation"></a><span data-ttu-id="f37ed-119">Inicializace ověření</span><span class="sxs-lookup"><span data-stu-id="f37ed-119">Initializing Validation</span></span>  
 <span data-ttu-id="f37ed-120">Po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen, jsou uvedeny dvě přetížený <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody použité k inicializaci stav <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="f37ed-121">Následují dva <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f37ed-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f37ed-122">Výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objektu a jeho počáteční stav přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, která použije <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt počáteční stav pro částečné ověření.</span><span class="sxs-lookup"><span data-stu-id="f37ed-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="f37ed-123">Obě <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody lze volat pouze ihned po <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl vytvořen nebo po volání <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>  
  
 <span data-ttu-id="f37ed-124">Příklad <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="f37ed-125">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="partial-validation"></a><span data-ttu-id="f37ed-126">Částečné ověřování</span><span class="sxs-lookup"><span data-stu-id="f37ed-126">Partial Validation</span></span>  
 <span data-ttu-id="f37ed-127"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metody, která použije <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicializuje <xref:System.Xml.Schema.XmlSchemaValidator> objekt počáteční stav pro částečné ověření.</span><span class="sxs-lookup"><span data-stu-id="f37ed-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="f37ed-128">V následujícím příkladu se <xref:System.Xml.Schema.XmlSchemaObject> inicializovaná pro částečné ověření pomocí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="f37ed-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f37ed-129">`orderNumber` Je předán element s schématu výběrem element schema podle <xref:System.Xml.XmlQualifiedName> v <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekce vrácené <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> objektu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="f37ed-130"><xref:System.Xml.Schema.XmlSchemaValidator> Objekt pak ověří tento konkrétní element.</span><span class="sxs-lookup"><span data-stu-id="f37ed-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>  
  
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
  
 <span data-ttu-id="f37ed-131">V příkladu vezme jako vstupní následující schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-131">The example takes the following XML schema as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="f37ed-132">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="adding-additional-schemas"></a><span data-ttu-id="f37ed-133">Přidání další schémata</span><span class="sxs-lookup"><span data-stu-id="f37ed-133">Adding Additional Schemas</span></span>  
 <span data-ttu-id="f37ed-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metodu <xref:System.Xml.Schema.XmlSchemaValidator> třída se používá pro přidání do sadu schémata používají při ověřování schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="f37ed-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda slouží k simulovat účinek zjištění schématu XML vložené v XML informační sadu, která je ověřována.</span><span class="sxs-lookup"><span data-stu-id="f37ed-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-136">Cílový obor názvů <xref:System.Xml.Schema.XmlSchema> parametr nesmí odpovídat žádné elementu nebo atributu již, se kterými <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
>   
>  <span data-ttu-id="f37ed-137">Pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> hodnota nebyl předán jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktoru, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda neprovede žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="f37ed-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>  
  
 <span data-ttu-id="f37ed-138">Výsledkem <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda je závislé na aktuální kontext uzlu XML během ověřování.</span><span class="sxs-lookup"><span data-stu-id="f37ed-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="f37ed-139">Další informace o ověření kontexty najdete v části "Ověření kontextu" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="f37ed-140">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="f37ed-141">Ověřování prvky, atributy a obsahu</span><span class="sxs-lookup"><span data-stu-id="f37ed-141">Validating Elements, Attributes, and Content</span></span>  
 <span data-ttu-id="f37ed-142"><xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje několik metod, které slouží k ověření prvky, atributy a obsah informační sadu XML pomocí schémat XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="f37ed-143">Následující tabulka popisuje každý z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="f37ed-143">The following table describes each of these methods.</span></span>  
  
|<span data-ttu-id="f37ed-144">Metoda</span><span class="sxs-lookup"><span data-stu-id="f37ed-144">Method</span></span>|<span data-ttu-id="f37ed-145">Popis</span><span class="sxs-lookup"><span data-stu-id="f37ed-145">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="f37ed-146">Ověří název elementu v aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-146">Validates the element name in the current context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="f37ed-147">Ověří atribut v aktuálním kontextu element nebo proti <xref:System.Xml.Schema.XmlSchemaAttribute> objekt předaný jako parametr, který se <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f37ed-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="f37ed-148">Ověřuje, zda všechny povinné atributy v kontextu elementu jsou prezentovat a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt, který chcete ověřit obsah podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="f37ed-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="f37ed-149">Ověří, zda je povolen v aktuálním kontextu element text a shromažďuje text pro ověření, pokud aktuálního elementu jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="f37ed-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="f37ed-150">Ověří, zda je povolen v aktuálním kontextu element prázdný a shromažďuje mezer pro ověření, zda má aktuálního elementu jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="f37ed-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="f37ed-151">Ověřuje, zda je platná podle jeho datového typu u elementů s jednoduchým obsahem textového obsahu elementu a ověřuje, zda je obsah aktuálního elementu dokončení u elementů se složitým obsahem.</span><span class="sxs-lookup"><span data-stu-id="f37ed-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="f37ed-152">Přeskočí ověření aktuálního obsahu elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objekt, který chcete ověřit obsah v kontextu nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="f37ed-153">Ukončí ověření a ověří identitu omezení pro celý dokument XML, zda <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> nastavena možnost ověření.</span><span class="sxs-lookup"><span data-stu-id="f37ed-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-154"><xref:System.Xml.Schema.XmlSchemaValidator> Třída má definované stavu přechodu, který vynucuje pořadí a výskytem volání do každé z metod popsaných v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="f37ed-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="f37ed-155">Určitém stavu přechod <xref:System.Xml.Schema.XmlSchemaValidator> třída je popsaný v části "Přechod stavu XmlSchemaValidator" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>  
  
 <span data-ttu-id="f37ed-156">Příklad metody použité k ověření prvky, atributy a obsah informační sadu XML podívejte se na příklad v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="f37ed-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="f37ed-157">Další informace o těchto metodách v tématu <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="f37ed-158">Ověření obsahu pomocí XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="f37ed-158">Validating Content Using an XmlValueGetter</span></span>  
 <span data-ttu-id="f37ed-159"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Slouží k předat hodnotu atributu, text nebo prázdný uzly jako typy Common Language Runtime (CLR) kompatibilní s typem jazyk definice schématu XML (XSD) atribut, text nebo mezer uzlu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="f37ed-160"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Je užitečné, pokud hodnota CLR atribut, text nebo mezer uzel je již k dispozici a zabraňuje náklady na jeho převodu `string` a pak ho znovu reparsing pro ověření.</span><span class="sxs-lookup"><span data-stu-id="f37ed-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>  
  
 <span data-ttu-id="f37ed-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, A <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> metody jsou přetížené a přijměte hodnotu atributu, text nebo prázdný uzly jako `string` nebo <xref:System.Xml.Schema.XmlValueGetter> `delegate`.</span><span class="sxs-lookup"><span data-stu-id="f37ed-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>  
  
 <span data-ttu-id="f37ed-162">Tyto metody <xref:System.Xml.Schema.XmlSchemaValidator> třída přijmout <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f37ed-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 <span data-ttu-id="f37ed-163">Následuje příklad <xref:System.Xml.Schema.XmlValueGetter> `delegate` převzaty z <xref:System.Xml.Schema.XmlSchemaValidator> příklad třídy v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="f37ed-164"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Vrátí hodnotu atributu jako <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="f37ed-165">Chcete-li to ověřit <xref:System.DateTime> objekt vrácený <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> objekt nejprve převeden na typ hodnoty (ValueType je výchozí mapování CLR pro typ XSD) pro datový typ atributu, a pak omezující vlastnosti kontroly na převedenou hodnota.</span><span class="sxs-lookup"><span data-stu-id="f37ed-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>  
  
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
  
 <span data-ttu-id="f37ed-166">Pro kompletní příklad, jak <xref:System.Xml.Schema.XmlValueGetter> `delegate`, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="f37ed-167">Další informace o <xref:System.Xml.Schema.XmlValueGetter> `delegate`, najdete v článku <xref:System.Xml.Schema.XmlValueGetter>, a <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="post-schema-validation-information"></a><span data-ttu-id="f37ed-168">Po-Schema--informace o ověření</span><span class="sxs-lookup"><span data-stu-id="f37ed-168">Post-Schema-Validation-Information</span></span>  
 <span data-ttu-id="f37ed-169"><xref:System.Xml.Schema.XmlSchemaInfo> Třída reprezentuje některé po-Schema-ověření-informace o uzlu XML ověřen <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="f37ed-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="f37ed-170">Různé metody <xref:System.Xml.Schema.XmlSchemaValidator> třída přijmout <xref:System.Xml.Schema.XmlSchemaInfo> objektu jako volitelný, (`null`) `out` parametr.</span><span class="sxs-lookup"><span data-stu-id="f37ed-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>  
  
 <span data-ttu-id="f37ed-171">Po úspěšném ověření vlastnosti <xref:System.Xml.Schema.XmlSchemaInfo> objektu se nastavují s výsledky ověření.</span><span class="sxs-lookup"><span data-stu-id="f37ed-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="f37ed-172">Například po úspěšné ověření použití atributu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> objektu je (Pokud je zadána) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, a <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> vlastnosti se nastavují s výsledky ověření .</span><span class="sxs-lookup"><span data-stu-id="f37ed-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>  
  
 <span data-ttu-id="f37ed-173">Následující <xref:System.Xml.Schema.XmlSchemaValidator> přijmout metody třídy <xref:System.Xml.Schema.XmlSchemaInfo> objektu jako výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="f37ed-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 <span data-ttu-id="f37ed-174">Pro kompletní příklad, jak <xref:System.Xml.Schema.XmlSchemaInfo> třídy, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="f37ed-175">Další informace o <xref:System.Xml.Schema.XmlSchemaInfo> naleznete <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="f37ed-176">Načítání očekávané částice, atributy a neurčené výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="f37ed-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>  
 <span data-ttu-id="f37ed-177"><xref:System.Xml.Schema.XmlSchemaValidator> Třída poskytuje <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody se načíst očekávaný částice, atributy a neurčené výchozí atributy v aktuálním kontextu ověřování.</span><span class="sxs-lookup"><span data-stu-id="f37ed-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>  
  
#### <a name="retrieving-expected-particles"></a><span data-ttu-id="f37ed-178">Načítání očekávané částice</span><span class="sxs-lookup"><span data-stu-id="f37ed-178">Retrieving Expected Particles</span></span>  
 <span data-ttu-id="f37ed-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaParticle> objekty, které obsahují očekávané částice v aktuálním kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="f37ed-180">Platný částice, které mohou být vráceny <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jsou instancemi třídy <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAny> třídy.</span><span class="sxs-lookup"><span data-stu-id="f37ed-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>  
  
 <span data-ttu-id="f37ed-181">Pokud je složku pro model obsahu `xs:sequence`, je vrácena pouze další částice v pořadí.</span><span class="sxs-lookup"><span data-stu-id="f37ed-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="f37ed-182">Pokud je složku pro model obsahu `xs:all` nebo `xs:choice`, pak jsou vráceny všechny platné částice, které mohou být za v aktuálním kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-183">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána hned po volání <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí všechny elementy globální.</span><span class="sxs-lookup"><span data-stu-id="f37ed-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>  
  
 <span data-ttu-id="f37ed-184">Například v XML schéma Definition Language (XSD) schématu a XML dokumentu následujících, po ověření `book` elementu, `book` element je aktuální kontext elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="f37ed-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `title` elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="f37ed-186">Pokud je kontext ověřování `title` elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="f37ed-187">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `title` element byl ověřen ale předtím, než `description` element byl ověřen, vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaElement> objekt reprezentující `description` element.</span><span class="sxs-lookup"><span data-stu-id="f37ed-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="f37ed-188">Pokud <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda je volána po `description` ověřila element pak vrátí pole obsahující jeden <xref:System.Xml.Schema.XmlSchemaAny> objekt reprezentující zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="f37ed-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>  
  
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
  
 <span data-ttu-id="f37ed-189">V příkladu vezme jako vstupní následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-189">The example takes the following XML as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="f37ed-190">V příkladu následující schéma XSD vezme jako vstupní.</span><span class="sxs-lookup"><span data-stu-id="f37ed-190">The example takes the following XSD schema as input.</span></span>  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-191">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na aktuální kontext ověřován.</span><span class="sxs-lookup"><span data-stu-id="f37ed-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="f37ed-192">Další informace najdete v části "Ověření kontextu" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-192">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="f37ed-193">Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="f37ed-194">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="f37ed-195">Načítání očekávané atributů</span><span class="sxs-lookup"><span data-stu-id="f37ed-195">Retrieving Expected Attributes</span></span>  
 <span data-ttu-id="f37ed-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda vrátí pole <xref:System.Xml.Schema.XmlSchemaAttribute> objekty, které obsahují očekávané atributy v aktuálním kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>  
  
 <span data-ttu-id="f37ed-197">V příkladu v úvodu, například <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda se používá k načtení všech atributů z `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>  
  
 <span data-ttu-id="f37ed-198">Když zavoláte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda ihned po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metoda, jsou vráceny všechny atributy, které může zobrazit v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="f37ed-199">Ale při volání <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda po jeden nebo více volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metoda, jsou vráceny atributy, které ještě nebyly byl ověřen pro aktuální element.</span><span class="sxs-lookup"><span data-stu-id="f37ed-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-200">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na aktuální kontext ověřován.</span><span class="sxs-lookup"><span data-stu-id="f37ed-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="f37ed-201">Další informace najdete v části "Ověření kontextu" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-201">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="f37ed-202">Příklad <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="f37ed-203">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="f37ed-204">Načítání neurčené výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="f37ed-204">Retrieving Unspecified Default Attributes</span></span>  
 <span data-ttu-id="f37ed-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda naplní <xref:System.Collections.ArrayList> zadaným <xref:System.Xml.Schema.XmlSchemaAttribute> objekty pro atributy s výchozími hodnotami, které nebyly ověřeny dříve pomocí <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metoda v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="f37ed-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda by měla být volána po volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metodu na jednotlivé atributy v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="f37ed-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda slouží k určení, co má být vložen do dokumentu XML během ověřování jsou výchozí atributy.</span><span class="sxs-lookup"><span data-stu-id="f37ed-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>  
  
 <span data-ttu-id="f37ed-208">Další informace o <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metodu, najdete v článku <xref:System.Xml.Schema.XmlSchemaValidator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="handling-schema-validation-events"></a><span data-ttu-id="f37ed-209">Zpracování událostí ověření schématu</span><span class="sxs-lookup"><span data-stu-id="f37ed-209">Handling Schema Validation Events</span></span>  
 <span data-ttu-id="f37ed-210">Schéma ověřování upozornění a chyb zjištěných při ověřování jsou zpracovávány <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> události <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="f37ed-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
 <span data-ttu-id="f37ed-211">Upozornění na ověření schématu mít <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning> a chyby ověřování schématu <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="f37ed-212">Pokud žádné <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> byl přiřazen, <xref:System.Xml.Schema.XmlSchemaValidationException> je vyvolána pro všechny chyby ověřování schématu s <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="f37ed-213">Však <xref:System.Xml.Schema.XmlSchemaValidationException> není pro schéma ověřování upozornění s vyvolána <xref:System.Xml.Schema.XmlSeverityType> hodnotu <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>  
  
 <span data-ttu-id="f37ed-214">Tady je příklad <xref:System.Xml.Schema.ValidationEventHandler> která přijme, schématu ověření upozornění a chyb zjištěných při ověřování schématu prováděné z příkladu v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>  
  
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
  
 <span data-ttu-id="f37ed-215">Pro kompletní příklad, jak <xref:System.Xml.Schema.ValidationEventHandler>, podívejte se na příklad v úvodu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="f37ed-216">Další informace najdete v tématu <xref:System.Xml.Schema.XmlSchemaInfo> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="f37ed-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="f37ed-217">Přechod stavu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="f37ed-217">XmlSchemaValidator State Transition</span></span>  
 <span data-ttu-id="f37ed-218"><xref:System.Xml.Schema.XmlSchemaValidator> Třída má definované stavu přechodu, který vynucuje pořadí a výskytem volání do každé metody použité k ověření prvky, atributy a obsah informační sadu XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
 <span data-ttu-id="f37ed-219">Následující tabulka popisuje přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třída a pořadí a výskytem volání metod, které lze provést v každém stavu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>  
  
|<span data-ttu-id="f37ed-220">Stav</span><span class="sxs-lookup"><span data-stu-id="f37ed-220">State</span></span>|<span data-ttu-id="f37ed-221">Přechod</span><span class="sxs-lookup"><span data-stu-id="f37ed-221">Transition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="f37ed-222">Ověření</span><span class="sxs-lookup"><span data-stu-id="f37ed-222">Validate</span></span>|<span data-ttu-id="f37ed-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel \*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="f37ed-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|  
|<span data-ttu-id="f37ed-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="f37ed-224">TopLevel</span></span>|<span data-ttu-id="f37ed-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; – Element</span><span class="sxs-lookup"><span data-stu-id="f37ed-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
|<span data-ttu-id="f37ed-226">Prvek</span><span class="sxs-lookup"><span data-stu-id="f37ed-226">Element</span></span>|<span data-ttu-id="f37ed-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\*)?</span><span class="sxs-lookup"><span data-stu-id="f37ed-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="f37ed-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="f37ed-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="f37ed-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="f37ed-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="f37ed-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Obsahu\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="f37ed-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|  
|<span data-ttu-id="f37ed-231">Obsah</span><span class="sxs-lookup"><span data-stu-id="f37ed-231">Content</span></span>|<span data-ttu-id="f37ed-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; – Element</span><span class="sxs-lookup"><span data-stu-id="f37ed-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-233"><xref:System.InvalidOperationException> Je vyvolána každou z metod v tabulce výše při volání metody je v nesprávné pořadí podle aktuálního stavu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
  
 <span data-ttu-id="f37ed-234">Výše uvedené tabulce přechod stavu pomocí interpunkčních znamének popisují metody a dalších stavy, které lze volat pro každý stav přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="f37ed-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="f37ed-235">Symboly použité jsou stejné symboly nalézt v odkazu standardy XML pro dokument typu definice (DTD).</span><span class="sxs-lookup"><span data-stu-id="f37ed-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>  
  
 <span data-ttu-id="f37ed-236">Následující tabulka popisuje vliv metody interpunkčních znamének najít v předchozí tabulce přechod stavu a dalších stavy, které lze volat pro každý stav v přechod stavu <xref:System.Xml.Schema.XmlSchemaValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="f37ed-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
|<span data-ttu-id="f37ed-237">Symbol</span><span class="sxs-lookup"><span data-stu-id="f37ed-237">Symbol</span></span>|<span data-ttu-id="f37ed-238">Popis</span><span class="sxs-lookup"><span data-stu-id="f37ed-238">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f37ed-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="f37ed-239">&#124;</span></span>|<span data-ttu-id="f37ed-240">Je možné volat metody nebo stavu (jeden před panelu) nebo jedna za ním.</span><span class="sxs-lookup"><span data-stu-id="f37ed-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|  
|<span data-ttu-id="f37ed-241">?</span><span class="sxs-lookup"><span data-stu-id="f37ed-241">?</span></span>|<span data-ttu-id="f37ed-242">Metoda nebo stavu, který předchází otazník je volitelný, ale pokud je volána ho lze volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="f37ed-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|  
|*|<span data-ttu-id="f37ed-243">Metoda nebo stavu, který předchází \* symbol je volitelná a lze volat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="f37ed-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|  
  
## <a name="validation-context"></a><span data-ttu-id="f37ed-244">Kontext ověřování</span><span class="sxs-lookup"><span data-stu-id="f37ed-244">Validation Context</span></span>  
 <span data-ttu-id="f37ed-245">Metody <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření prvky, atributy a obsah informační sadu XML, změňte ověření kontextu <xref:System.Xml.Schema.XmlSchemaValidator> objektu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="f37ed-246">Například <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> metoda přeskočí ověření aktuálního obsahu elementu a připraví <xref:System.Xml.Schema.XmlSchemaValidator> objektu ověřování obsahu v kontextu nadřazeného elementu; je ekvivalentní k přeskočení ověření pro všechny podřízené objekty aktuálního elementu a pak volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f37ed-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>  
  
 <span data-ttu-id="f37ed-247">Výsledky <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, a <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> třídy jsou závislé na aktuální kontext ověřován.</span><span class="sxs-lookup"><span data-stu-id="f37ed-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>  
  
 <span data-ttu-id="f37ed-248">Následující tabulka popisuje výsledky volání těchto metod po volání jedné z metod <xref:System.Xml.Schema.XmlSchemaValidator> třídu sloužící k ověření prvky, atributy a obsah informační sadu XML.</span><span class="sxs-lookup"><span data-stu-id="f37ed-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
|<span data-ttu-id="f37ed-249">Metoda</span><span class="sxs-lookup"><span data-stu-id="f37ed-249">Method</span></span>|<span data-ttu-id="f37ed-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="f37ed-250">GetExpectedParticles</span></span>|<span data-ttu-id="f37ed-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="f37ed-251">GetExpectedAttributes</span></span>|<span data-ttu-id="f37ed-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="f37ed-252">AddSchema</span></span>|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="f37ed-253">Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pole obsahující všechny globální elementy.</span><span class="sxs-lookup"><span data-stu-id="f37ed-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="f37ed-254">Pokud přetížené <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, která přijímá <xref:System.Xml.Schema.XmlSchemaObject> k chybě při inicializaci částečné ověřování elementu, se nazývá parametr <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí pouze prvek, ke kterému <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="f37ed-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="f37ed-255">Pokud výchozí <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda je volána, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="f37ed-256">Pokud přetížení <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, která použije <xref:System.Xml.Schema.XmlSchemaObject> k chybě při inicializaci částečné ověřování atributu, se nazývá parametr <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí pouze atribut, na kterou <xref:System.Xml.Schema.XmlSchemaValidator> objekt byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="f37ed-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="f37ed-257">Přidá schéma tak, aby <xref:System.Xml.Schema.XmlSchemaSet> z <xref:System.Xml.Schema.XmlSchemaValidator> objektu, pokud má žádné předběžného zpracování chyby.</span><span class="sxs-lookup"><span data-stu-id="f37ed-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="f37ed-258">Pokud element kontextu je platný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů očekáván jako podřízené objekty daného elementu kontextu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="f37ed-259">Pokud element kontextu je neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="f37ed-260">Pokud element kontextu je platný a pokud bez volání <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> byl dříve proveden, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam hodnot všechny atributy, které jsou definované v kontextu elementu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="f37ed-261">Pokud již byly ověřeny některé atributy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam hodnot zbývající atributy, které má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="f37ed-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="f37ed-262">Pokud element kontextu je neplatný, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="f37ed-263">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-263">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="f37ed-264">Pokud je atribut kontext atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="f37ed-265">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů očekávání jako první podřízený element kontextu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="f37ed-266">Pokud je atribut kontext atribut nejvyšší úrovně <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="f37ed-267">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí seznam zbývající atributů má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="f37ed-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="f37ed-268">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-268">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="f37ed-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů očekávání jako první podřízený element kontextu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="f37ed-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí seznam hodnot požadované a volitelné atributy, které ještě mají být ověřen pro element kontextu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="f37ed-271">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-271">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="f37ed-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů očekávání jako první podřízený element kontextu.</span><span class="sxs-lookup"><span data-stu-id="f37ed-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="f37ed-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="f37ed-274">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-274">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="f37ed-275">Pokud je Přimíchán element kontextu contentType, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů v další pozice se očekává.</span><span class="sxs-lookup"><span data-stu-id="f37ed-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="f37ed-276">Pokud je element kontextu contentType typu TextOnly nebo je prázdná, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="f37ed-277">Pokud je element kontextu contentType ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů v další pozice ale chybu ověření byl očekáván již došlo.</span><span class="sxs-lookup"><span data-stu-id="f37ed-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="f37ed-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí element kontextu seznam atributů nebyl ověřen.</span><span class="sxs-lookup"><span data-stu-id="f37ed-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="f37ed-279">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-279">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="f37ed-280">Pokud mezer kontextu je nejvyšší úrovně mezer <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="f37ed-281">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="f37ed-282">Pokud mezer kontextu je nejvyšší úrovně mezer <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="f37ed-283">V opačném případě <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> chování metody jsou stejné jako v <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="f37ed-284">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-284">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="f37ed-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Vrátí pořadí elementů byl očekáván po elementu kontextu (možné na stejné úrovni).</span><span class="sxs-lookup"><span data-stu-id="f37ed-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="f37ed-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Vrátí element kontextu seznam atributů nebyl ověřen.</span><span class="sxs-lookup"><span data-stu-id="f37ed-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="f37ed-287">Pokud element kontextu nemá nadřazený pak <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> vrací prázdný seznam (element kontextu je nadřazená aktuálního elementu, na kterém <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> byla volána).</span><span class="sxs-lookup"><span data-stu-id="f37ed-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="f37ed-288">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-288">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="f37ed-289">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="f37ed-290">Stejné jako <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="f37ed-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="f37ed-291">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-291">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="f37ed-292">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-292">Returns an empty array.</span></span>|<span data-ttu-id="f37ed-293">Vrátí prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f37ed-293">Returns an empty array.</span></span>|<span data-ttu-id="f37ed-294">Stejné jako výše.</span><span class="sxs-lookup"><span data-stu-id="f37ed-294">Same as above.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f37ed-295">Hodnot vrácených různé vlastnosti <xref:System.Xml.Schema.XmlSchemaValidator> třídy nejsou změněna voláním některou z metod v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="f37ed-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37ed-296">Viz také</span><span class="sxs-lookup"><span data-stu-id="f37ed-296">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaValidator>
