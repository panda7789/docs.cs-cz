---
title: Atributy, které řídí serializaci zakódovanou v protokolu SOAP
description: V tomto článku jsou uvedeny speciální sady atributů, které jsou k dispozici v oboru názvů System. XML. Serialization, který je nezbytný pro dodržení specifikace protokolu SOAP.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: d9a4631189d348c02ab36054257a54c9c4673018
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289665"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="2a593-103">Atributy, které řídí serializaci zakódovanou v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="2a593-103">Attributes That Control Encoded SOAP Serialization</span></span>

<span data-ttu-id="2a593-104">Dokument konsorcium World Wide Web (W3C) s názvem [Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) obsahuje volitelný oddíl (oddíl 5), který popisuje, jak lze kódovat parametry protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="2a593-104">The World Wide Web Consortium (W3C) document named [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="2a593-105">Pro dodržení oddílu 5 specifikace musíte použít speciální sadu atributů, které se nacházejí v <xref:System.Xml.Serialization> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2a593-105">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="2a593-106">Tyto atributy v závislosti na třídy a členy třídy aplikovat a pak <xref:System.Xml.Serialization.XmlSerializer> k serializaci instancí třídy nebo tříd.</span><span class="sxs-lookup"><span data-stu-id="2a593-106">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>

<span data-ttu-id="2a593-107">V následující tabulce jsou uvedeny atributy, kde je lze použít, a jejich význam.</span><span class="sxs-lookup"><span data-stu-id="2a593-107">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="2a593-108">Další informace o použití těchto atributů pro řízení serializace XML naleznete v tématu [How to: serializovat objekt jako datový proud XML s kódováním SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) a [Postupy: přepsání serializace XML](how-to-override-encoded-soap-xml-serialization.md)s kódováním.</span><span class="sxs-lookup"><span data-stu-id="2a593-108">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](how-to-override-encoded-soap-xml-serialization.md).</span></span>

<span data-ttu-id="2a593-109">Další informace o atributech naleznete v tématu [Attributes](../attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a593-109">For more information about attributes, see [Attributes](../attributes/index.md).</span></span>

|<span data-ttu-id="2a593-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="2a593-110">Attribute</span></span>|<span data-ttu-id="2a593-111">Platí pro</span><span class="sxs-lookup"><span data-stu-id="2a593-111">Applies to</span></span>|<span data-ttu-id="2a593-112">Určuje</span><span class="sxs-lookup"><span data-stu-id="2a593-112">Specifies</span></span>|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="2a593-113">Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2a593-113">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="2a593-114">Člen třídy bude serializována jako atribut XML.</span><span class="sxs-lookup"><span data-stu-id="2a593-114">The class member will be serialized as an XML attribute.</span></span>|
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="2a593-115">Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2a593-115">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="2a593-116">Třída bude serializována jako XML element.</span><span class="sxs-lookup"><span data-stu-id="2a593-116">The class will be serialized as an XML element.</span></span>|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="2a593-117">Veřejné pole, které je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="2a593-117">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="2a593-118">Název elementu člen výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="2a593-118">The element name of an enumeration member.</span></span>|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="2a593-119">Veřejné vlastnosti a pole.</span><span class="sxs-lookup"><span data-stu-id="2a593-119">Public properties and fields.</span></span>|<span data-ttu-id="2a593-120">Vlastnosti nebo pole mají být ignorovány, pokud je serializována třídu obsahující.</span><span class="sxs-lookup"><span data-stu-id="2a593-120">The property or field should be ignored when the containing class is serialized.</span></span>|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="2a593-121">Veřejná odvozené třídy prohlášení a veřejné metody pro dokumenty služby popis jazyka WSDL (Web).</span><span class="sxs-lookup"><span data-stu-id="2a593-121">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="2a593-122">Typ by měly být zahrnuty při generování schémat (Chcete-li rozpoznán po serializován).</span><span class="sxs-lookup"><span data-stu-id="2a593-122">The type should be included when generating schemas (to be recognized when serialized).</span></span>|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="2a593-123">Deklarace veřejných tříd.</span><span class="sxs-lookup"><span data-stu-id="2a593-123">Public class declarations.</span></span>|<span data-ttu-id="2a593-124">Třída by měla být serializován jako typ objektu XML.</span><span class="sxs-lookup"><span data-stu-id="2a593-124">The class should be serialized as an XML type.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2a593-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a593-125">See also</span></span>

- [<span data-ttu-id="2a593-126">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="2a593-126">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="2a593-127">Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="2a593-127">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [<span data-ttu-id="2a593-128">Postupy: Přepsání serializace XML zakódované v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="2a593-128">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
- [<span data-ttu-id="2a593-129">Atributy</span><span class="sxs-lookup"><span data-stu-id="2a593-129">Attributes</span></span>](../attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="2a593-130">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="2a593-130">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="2a593-131">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="2a593-131">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
