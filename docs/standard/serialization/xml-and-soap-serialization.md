---
title: XML a serializace protokolu SOAP
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
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 006727e70c58834a4e628f584a28302a62363844
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="d9f8c-102">XML a serializace protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d9f8c-102">XML and SOAP Serialization</span></span>
<span data-ttu-id="d9f8c-103">Převede serializace XML (serializuje) veřejné polí a vlastností objektu, nebo parametry a návratovými hodnotami metod do datový proud XML, který odpovídá určitého dokumentu definition language (XSD) schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="d9f8c-104">Serializace XML výsledkem silného typu třídy s veřejné vlastnosti a pole, které jsou převedeny na sériového formátu (v tomto případě XML) pro uložení nebo přenos.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>  
  
 <span data-ttu-id="d9f8c-105">Protože kód XML je otevřený standard, může být zpracována datový proud XML ve všech aplikacích, podle potřeby, bez ohledu na platformu.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="d9f8c-106">Můžete například webové služby XML vytvořené pomocí technologie ASP.NET použití <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření datové proudy XML, který vkládá data mezi aplikací webové služby XML v rámci Internetu nebo v těchto sítích.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="d9f8c-107">Deserializace naopak přebírá takové datový proud XML a rekonstruuje objektu.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>  
  
 <span data-ttu-id="d9f8c-108">Serializace XML lze také použít k serializaci objektů do datových proudů XML, které odpovídají specifikaci protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="d9f8c-109">Protokol SOAP je protokol založený na formát XML, který je určen speciálně k přenosu volání procedur pomocí jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>  
  
 <span data-ttu-id="d9f8c-110">K serializaci nebo deserializaci objektů, použijte <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="d9f8c-111">Chcete-li vytvořit třídy k serializaci, použijte nástroj definici schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9f8c-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d9f8c-112">In This Section</span></span>  
 [<span data-ttu-id="d9f8c-113">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="d9f8c-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 <span data-ttu-id="d9f8c-114">Poskytuje obecné definici serializaci, zejména serializace XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-114">Provides a general definition of serialization, particularly XML serialization.</span></span>  
  
 [<span data-ttu-id="d9f8c-115">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="d9f8c-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 <span data-ttu-id="d9f8c-116">Obsahuje podrobné pokyny pro serializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-116">Provides step-by-step instructions for serializing an object.</span></span>  
  
 [<span data-ttu-id="d9f8c-117">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="d9f8c-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 <span data-ttu-id="d9f8c-118">Obsahuje podrobné pokyny pro deserializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-118">Provides step-by-step instructions for deserializing an object.</span></span>  
  
 [<span data-ttu-id="d9f8c-119">Příklady serializace XML</span><span class="sxs-lookup"><span data-stu-id="d9f8c-119">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 <span data-ttu-id="d9f8c-120">Obsahuje příklady, které ukazují základy serializace XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-120">Provides examples that demonstrate the basics of XML serialization.</span></span>  
  
 [<span data-ttu-id="d9f8c-121">Nástroj pro definici schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="d9f8c-121">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 <span data-ttu-id="d9f8c-122">Popisuje, jak používat nástroj definici schématu XML k vytvoření třídy, které splňovat konkrétní jazyk (XSD) schématu definice schématu XML nebo ke generování schématu XML z soubor DLL.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>  
  
 [<span data-ttu-id="d9f8c-123">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="d9f8c-123">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 <span data-ttu-id="d9f8c-124">Popisuje, jak řídit serializace pomocí atributů.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-124">Describes how to control serialization by using attributes.</span></span>  
  
 [<span data-ttu-id="d9f8c-125">Seznam atributů řídících serializaci XML</span><span class="sxs-lookup"><span data-stu-id="d9f8c-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 <span data-ttu-id="d9f8c-126">Seznam atributů, které se používají k řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-126">Lists the attributes that are used to control XML serialization.</span></span>  
  
 [<span data-ttu-id="d9f8c-127">Postupy: Zadání alternativního názvu elementu pro XML stream</span><span class="sxs-lookup"><span data-stu-id="d9f8c-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 <span data-ttu-id="d9f8c-128">Uvede případě rozšířeného scénáře ukázkami, jak ke generování více datové proudy XML přepsáním serializace.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>  
  
 [<span data-ttu-id="d9f8c-129">Postupy: Řízení serializace odvozených tříd</span><span class="sxs-lookup"><span data-stu-id="d9f8c-129">How to: Control Serialization of Derived Classes</span></span>](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 <span data-ttu-id="d9f8c-130">Obsahuje příklad toho, jak řídit serializace odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-130">Provides an example of how to control the serialization of derived classes.</span></span>  
  
 [<span data-ttu-id="d9f8c-131">Postupy: Kvalifikace názvů elementů a atributů XML</span><span class="sxs-lookup"><span data-stu-id="d9f8c-131">How to: Qualify XML Element and XML Attribute Names</span></span>](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 <span data-ttu-id="d9f8c-132">Popisuje, jak lze definovat a určit tak, jak v XML, které se používají obory názvů v datovém proudu XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>  
  
 [<span data-ttu-id="d9f8c-133">Serializace XML pomocí webových služeb XML</span><span class="sxs-lookup"><span data-stu-id="d9f8c-133">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 <span data-ttu-id="d9f8c-134">Vysvětluje, jak serializace XML se používá v webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-134">Explains how XML serialization is used in XML Web services.</span></span>  
  
 [<span data-ttu-id="d9f8c-135">Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d9f8c-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <span data-ttu-id="d9f8c-136">Popisuje, jak lze použít <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření kódovaného datové proudy SOAP XML, které odpovídají část 5 W3c (www.w3.org) dokumentu s názvem "Simple Object Access Protocol (SOAP) 1.1."</span><span class="sxs-lookup"><span data-stu-id="d9f8c-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1."</span></span>  
  
 [<span data-ttu-id="d9f8c-137">Postupy: Přepsání serializace XML zakódované v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d9f8c-137">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 <span data-ttu-id="d9f8c-138">Popisuje proces pro přepsání XML serializaci objektů jako zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>  
  
 [<span data-ttu-id="d9f8c-139">Seznam atributů řídících serializaci zakódovanou v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="d9f8c-139">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 <span data-ttu-id="d9f8c-140">Seznam atributů, které se používají k řízení kódováním SOAP serializace.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>  
  
 [<span data-ttu-id="d9f8c-141">\<System.XML.Serialization > elementu</span><span class="sxs-lookup"><span data-stu-id="d9f8c-141">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="d9f8c-142">Element konfigurace nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-142">The top-level configuration element for controlling XML serialization.</span></span>  
  
 [<span data-ttu-id="d9f8c-143">\<dateTimeSerialization > elementu</span><span class="sxs-lookup"><span data-stu-id="d9f8c-143">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 <span data-ttu-id="d9f8c-144">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 [<span data-ttu-id="d9f8c-145">\<schemaImporterExtensions > elementu</span><span class="sxs-lookup"><span data-stu-id="d9f8c-145">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 <span data-ttu-id="d9f8c-146">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
 [<span data-ttu-id="d9f8c-147">\<Přidat > elementu pro \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="d9f8c-147">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <span data-ttu-id="d9f8c-148">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9f8c-149">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d9f8c-149">Related Sections</span></span>  
 [<span data-ttu-id="d9f8c-150">Vývoj pro pokročilé technologie</span><span class="sxs-lookup"><span data-stu-id="d9f8c-150">Advanced Development Technologies</span></span>](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 <span data-ttu-id="d9f8c-151">Obsahuje odkazy na další informace o sofistikované vývojářské úlohy a techniky v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-151">Provides links to more information on sophisticated development tasks and techniques in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="d9f8c-152">Webové služby XML vytvořený pomocí technologie ASP.NET a klienty webové služby XML</span><span class="sxs-lookup"><span data-stu-id="d9f8c-152">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="d9f8c-153">Obsahuje témata, která popisují a popisují, jak program webové služby XML pomocí technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d9f8c-153">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f8c-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9f8c-154">See Also</span></span>  
 [<span data-ttu-id="d9f8c-155">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="d9f8c-155">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
