---
title: "Atributy, které řídí serializace kódovaného protokolu SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 358b635ee74699d9d427e8fac23fabd70c6cfa98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="d59cd-102">Atributy, které řídí serializace kódovaného protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d59cd-102">Attributes That Control Encoded SOAP Serialization</span></span> 
<span data-ttu-id="d59cd-103">Dokument World Wide Web Consortium (www.w3.org) s názvem "Simple Object Access Protocol (SOAP) 1.1" obsahuje volitelný oddíl (část 5), který popisuje, jak můžete zakódovat parametry protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d59cd-103">The World Wide Web Consortium (www.w3.org) document named "Simple Object Access Protocol (SOAP) 1.1" contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="d59cd-104">Tak, aby odpovídala část 5 specifikace, musíte použít speciální sadu atributů, které jsou součástí <xref:System.Xml.Serialization> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d59cd-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="d59cd-105">Tyto atributy v závislosti na třídy a členy třídy aplikovat a pak <xref:System.Xml.Serialization.XmlSerializer> k serializaci instancí třídy nebo tříd.</span><span class="sxs-lookup"><span data-stu-id="d59cd-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>  
  
 <span data-ttu-id="d59cd-106">V následující tabulce jsou uvedeny atributy, kde je lze použít, a jejich význam.</span><span class="sxs-lookup"><span data-stu-id="d59cd-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="d59cd-107">Další informace o použití těchto atributů k řízení serializace XML, najdete v části [postup: serializovat objekt jako protokolu SOAP-datový proud XML kódováno](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) a [postupy: přepsání kódovaný serializace XML protokolu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="d59cd-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span></span>  
  
 <span data-ttu-id="d59cd-108">Další informace o atributech najdete v tématu [atributy](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="d59cd-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>  
  
|<span data-ttu-id="d59cd-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="d59cd-109">Attribute</span></span>|<span data-ttu-id="d59cd-110">Platí pro</span><span class="sxs-lookup"><span data-stu-id="d59cd-110">Applies to</span></span>|<span data-ttu-id="d59cd-111">Určuje</span><span class="sxs-lookup"><span data-stu-id="d59cd-111">Specifies</span></span>|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="d59cd-112">Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d59cd-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="d59cd-113">Člen třídy bude serializována jako atribut XML.</span><span class="sxs-lookup"><span data-stu-id="d59cd-113">The class member will be serialized as an XML attribute.</span></span>|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="d59cd-114">Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d59cd-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="d59cd-115">Třída bude serializována jako XML element.</span><span class="sxs-lookup"><span data-stu-id="d59cd-115">The class will be serialized as an XML element.</span></span>|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="d59cd-116">Veřejné pole, které je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="d59cd-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="d59cd-117">Název elementu člen výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="d59cd-117">The element name of an enumeration member.</span></span>|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="d59cd-118">Veřejné vlastnosti a pole.</span><span class="sxs-lookup"><span data-stu-id="d59cd-118">Public properties and fields.</span></span>|<span data-ttu-id="d59cd-119">Vlastnosti nebo pole mají být ignorovány, pokud je serializována třídu obsahující.</span><span class="sxs-lookup"><span data-stu-id="d59cd-119">The property or field should be ignored when the containing class is serialized.</span></span>|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="d59cd-120">Veřejná odvozené třídy prohlášení a veřejné metody pro dokumenty služby popis jazyka WSDL (Web).</span><span class="sxs-lookup"><span data-stu-id="d59cd-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="d59cd-121">Typ by měly být zahrnuty při generování schémat (Chcete-li rozpoznán po serializován).</span><span class="sxs-lookup"><span data-stu-id="d59cd-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="d59cd-122">Deklarace veřejných tříd.</span><span class="sxs-lookup"><span data-stu-id="d59cd-122">Public class declarations.</span></span>|<span data-ttu-id="d59cd-123">Třída by měla být serializován jako typ objektu XML.</span><span class="sxs-lookup"><span data-stu-id="d59cd-123">The class should be serialized as an XML type.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d59cd-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d59cd-124">See Also</span></span>  
 [<span data-ttu-id="d59cd-125">XML a serializace protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d59cd-125">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="d59cd-126">Postupy: serializaci objektu jako datový proud XML kódováním protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d59cd-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [<span data-ttu-id="d59cd-127">Postupy: potlačení serializace XML kódovaného protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d59cd-127">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [<span data-ttu-id="d59cd-128">Atributy</span><span class="sxs-lookup"><span data-stu-id="d59cd-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="d59cd-129">Postupy: serializaci objektu</span><span class="sxs-lookup"><span data-stu-id="d59cd-129">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="d59cd-130">Postupy: deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="d59cd-130">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
