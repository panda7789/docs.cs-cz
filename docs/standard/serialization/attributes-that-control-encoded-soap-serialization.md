---
title: Atributy, které řídí serializaci zakódovanou v protokolu SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 2961d9abc6c32e78b5a61e8f2bbea5cfcf6677bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794937"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="dcfe8-102">Atributy, které řídí serializaci zakódovanou v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="dcfe8-102">Attributes That Control Encoded SOAP Serialization</span></span>

<span data-ttu-id="dcfe8-103">Dokument konsorcium World Wide Web (W3C) s názvem [Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) obsahuje volitelný oddíl (oddíl 5), který popisuje, jak lze kódovat parametry protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-103">The World Wide Web Consortium (W3C) document named [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="dcfe8-104">Pro dodržení oddílu 5 specifikace musíte použít speciální sadu atributů, které se <xref:System.Xml.Serialization> nacházejí v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="dcfe8-105">Tyto atributy v závislosti na třídy a členy třídy aplikovat a pak <xref:System.Xml.Serialization.XmlSerializer> k serializaci instancí třídy nebo tříd.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>

<span data-ttu-id="dcfe8-106">V následující tabulce jsou uvedeny atributy, kde je lze použít, a jejich význam.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="dcfe8-107">Další informace o použití těchto atributů pro řízení serializace XML naleznete v tématu [How to: serializovat objekt jako datový proud XML s kódováním SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) a [Postupy: přepsání serializace XML](how-to-override-encoded-soap-xml-serialization.md)s kódováním.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](how-to-override-encoded-soap-xml-serialization.md).</span></span>

<span data-ttu-id="dcfe8-108">Další informace o atributech naleznete v tématu [Attributes](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="dcfe8-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>

|<span data-ttu-id="dcfe8-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="dcfe8-109">Attribute</span></span>|<span data-ttu-id="dcfe8-110">Platí pro</span><span class="sxs-lookup"><span data-stu-id="dcfe8-110">Applies to</span></span>|<span data-ttu-id="dcfe8-111">Určuje</span><span class="sxs-lookup"><span data-stu-id="dcfe8-111">Specifies</span></span>|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="dcfe8-112">Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="dcfe8-113">Člen třídy bude serializována jako atribut XML.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-113">The class member will be serialized as an XML attribute.</span></span>|
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="dcfe8-114">Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="dcfe8-115">Třída bude serializována jako XML element.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-115">The class will be serialized as an XML element.</span></span>|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="dcfe8-116">Veřejné pole, které je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="dcfe8-117">Název elementu člen výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-117">The element name of an enumeration member.</span></span>|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="dcfe8-118">Veřejné vlastnosti a pole.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-118">Public properties and fields.</span></span>|<span data-ttu-id="dcfe8-119">Vlastnosti nebo pole mají být ignorovány, pokud je serializována třídu obsahující.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-119">The property or field should be ignored when the containing class is serialized.</span></span>|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="dcfe8-120">Veřejná odvozené třídy prohlášení a veřejné metody pro dokumenty služby popis jazyka WSDL (Web).</span><span class="sxs-lookup"><span data-stu-id="dcfe8-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="dcfe8-121">Typ by měly být zahrnuty při generování schémat (Chcete-li rozpoznán po serializován).</span><span class="sxs-lookup"><span data-stu-id="dcfe8-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="dcfe8-122">Deklarace veřejných tříd.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-122">Public class declarations.</span></span>|<span data-ttu-id="dcfe8-123">Třída by měla být serializován jako typ objektu XML.</span><span class="sxs-lookup"><span data-stu-id="dcfe8-123">The class should be serialized as an XML type.</span></span>|

## <a name="see-also"></a><span data-ttu-id="dcfe8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcfe8-124">See also</span></span>

- [<span data-ttu-id="dcfe8-125">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="dcfe8-125">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="dcfe8-126">Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="dcfe8-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [<span data-ttu-id="dcfe8-127">Postupy: Přepsání serializace XML zakódované v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="dcfe8-127">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
- [<span data-ttu-id="dcfe8-128">Atributy</span><span class="sxs-lookup"><span data-stu-id="dcfe8-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="dcfe8-129">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="dcfe8-129">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="dcfe8-130">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="dcfe8-130">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
