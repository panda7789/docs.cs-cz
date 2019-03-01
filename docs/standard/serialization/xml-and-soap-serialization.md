---
title: Serializace XML a SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965615"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="57f56-102">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="57f56-102">XML and SOAP Serialization</span></span>

<span data-ttu-id="57f56-103">Převede serializace XML (serializuje) veřejné polí a vlastností objektu, nebo parametry a návratovými hodnotami metod do datový proud XML, který odpovídá určitého dokumentu definition language (XSD) schématu XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="57f56-104">Serializace XML výsledkem silného typu třídy s veřejné vlastnosti a pole, které jsou převedeny na sériového formátu (v tomto případě XML) pro uložení nebo přenos.</span><span class="sxs-lookup"><span data-stu-id="57f56-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="57f56-105">Protože kód XML je otevřený standard, může být zpracována datový proud XML ve všech aplikacích, podle potřeby, bez ohledu na platformu.</span><span class="sxs-lookup"><span data-stu-id="57f56-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="57f56-106">Můžete například webové služby XML vytvořené pomocí technologie ASP.NET použití <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření datové proudy XML, který vkládá data mezi aplikací webové služby XML v rámci Internetu nebo v těchto sítích.</span><span class="sxs-lookup"><span data-stu-id="57f56-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="57f56-107">Deserializace naopak přebírá takové datový proud XML a rekonstruuje objektu.</span><span class="sxs-lookup"><span data-stu-id="57f56-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="57f56-108">Serializace XML lze také použít k serializaci objektů do datových proudů XML, které odpovídají specifikaci protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="57f56-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="57f56-109">Protokol SOAP je protokol založený na formát XML, který je určen speciálně k přenosu volání procedur pomocí jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="57f56-110">K serializaci nebo deserializaci objektů, použijte <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="57f56-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="57f56-111">Chcete-li vytvořit třídy k serializaci, použijte nástroj definici schématu XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="57f56-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="57f56-112">In This Section</span></span>

[<span data-ttu-id="57f56-113">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="57f56-113">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)  
<span data-ttu-id="57f56-114">Poskytuje obecné definici serializaci, zejména serializace XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-114">Provides a general definition of serialization, particularly XML serialization.</span></span>

[<span data-ttu-id="57f56-115">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="57f56-115">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)  
<span data-ttu-id="57f56-116">Obsahuje podrobné pokyny pro serializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="57f56-116">Provides step-by-step instructions for serializing an object.</span></span>

[<span data-ttu-id="57f56-117">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="57f56-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)  
<span data-ttu-id="57f56-118">Obsahuje podrobné pokyny pro deserializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="57f56-118">Provides step-by-step instructions for deserializing an object.</span></span>

[<span data-ttu-id="57f56-119">Příklady serializace XML</span><span class="sxs-lookup"><span data-stu-id="57f56-119">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)  
<span data-ttu-id="57f56-120">Poskytuje příklady, které ukazují základní informace o serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-120">Provides examples that demonstrate the basics of XML serialization.</span></span>

[<span data-ttu-id="57f56-121">Nástroj pro definici schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="57f56-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)  
<span data-ttu-id="57f56-122">Popisuje, jak používat nástroj definici schématu XML k vytvoření třídy, které splňovat konkrétní jazyk (XSD) schématu definice schématu XML nebo ke generování schématu XML z soubor DLL.</span><span class="sxs-lookup"><span data-stu-id="57f56-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>

[<span data-ttu-id="57f56-123">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="57f56-123">Controlling XML Serialization Using Attributes</span></span>](controlling-xml-serialization-using-attributes.md)  
<span data-ttu-id="57f56-124">Popisuje, jak řídit serializace pomocí atributů.</span><span class="sxs-lookup"><span data-stu-id="57f56-124">Describes how to control serialization by using attributes.</span></span>

[<span data-ttu-id="57f56-125">Seznam atributů řídících serializaci XML</span><span class="sxs-lookup"><span data-stu-id="57f56-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)  
<span data-ttu-id="57f56-126">Seznam atributů, které se používají k řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-126">Lists the attributes that are used to control XML serialization.</span></span>

[<span data-ttu-id="57f56-127">Postupy: Určení alternativního názvu elementu pro Stream XML</span><span class="sxs-lookup"><span data-stu-id="57f56-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
<span data-ttu-id="57f56-128">Uvede případě rozšířeného scénáře ukázkami, jak ke generování více datové proudy XML přepsáním serializace.</span><span class="sxs-lookup"><span data-stu-id="57f56-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>

[<span data-ttu-id="57f56-129">Postupy: Řízení serializace odvozených tříd</span><span class="sxs-lookup"><span data-stu-id="57f56-129">How to: Control Serialization of Derived Classes</span></span>](how-to-control-serialization-of-derived-classes.md)  
<span data-ttu-id="57f56-130">Obsahuje příklad toho, jak řídit serializace odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="57f56-130">Provides an example of how to control the serialization of derived classes.</span></span>

[<span data-ttu-id="57f56-131">Postupy: Kvalifikovat názvy atributů XML a elementu XML</span><span class="sxs-lookup"><span data-stu-id="57f56-131">How to: Qualify XML Element and XML Attribute Names</span></span>](how-to-qualify-xml-element-and-xml-attribute-names.md)  
<span data-ttu-id="57f56-132">Popisuje, jak lze definovat a určit tak, jak v XML, které se používají obory názvů v datovém proudu XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>

[<span data-ttu-id="57f56-133">Serializace XML pomocí webových služeb XML</span><span class="sxs-lookup"><span data-stu-id="57f56-133">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)  
<span data-ttu-id="57f56-134">Vysvětluje, jak serializace XML se používá v webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-134">Explains how XML serialization is used in XML Web services.</span></span>

[<span data-ttu-id="57f56-135">Postupy: Serializace objektu jako XML kódováním protokolu SOAP Stream</span><span class="sxs-lookup"><span data-stu-id="57f56-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
<span data-ttu-id="57f56-136">Popisuje způsob použití <xref:System.Xml.Serialization.XmlSerializer> třídy za účelem vytvoření kódovaného datové proudy SOAP XML, které odpovídají část 5 World Wide Web Consortium (W3C) dokumentu s názvem [jednoduchý objekt přístup protokolu (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span><span class="sxs-lookup"><span data-stu-id="57f56-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span></span>

[<span data-ttu-id="57f56-137">Postupy: Přepsat kódovaný protokol SOAP serializace XML</span><span class="sxs-lookup"><span data-stu-id="57f56-137">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)  
<span data-ttu-id="57f56-138">Popisuje proces pro přepsání XML serializaci objektů jako zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="57f56-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>

[<span data-ttu-id="57f56-139">Seznam atributů řídících serializaci zakódovanou v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="57f56-139">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)  
<span data-ttu-id="57f56-140">Seznam atributů, které se používají k řízení kódováním SOAP serializace.</span><span class="sxs-lookup"><span data-stu-id="57f56-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>

[<span data-ttu-id="57f56-141">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="57f56-141">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)  
<span data-ttu-id="57f56-142">Element konfigurace nejvyšší úrovně pro řízení serializace XML.</span><span class="sxs-lookup"><span data-stu-id="57f56-142">The top-level configuration element for controlling XML serialization.</span></span>

[<span data-ttu-id="57f56-143">\<dateTimeSerialization > – Element</span><span class="sxs-lookup"><span data-stu-id="57f56-143">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)  
<span data-ttu-id="57f56-144">Určuje režim serializace <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="57f56-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>

[<span data-ttu-id="57f56-145">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="57f56-145">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)  
<span data-ttu-id="57f56-146">Obsahuje typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="57f56-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

[<span data-ttu-id="57f56-147">\<Přidat > – Element pro \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="57f56-147">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)  
<span data-ttu-id="57f56-148">Přidá typy, které jsou používány <xref:System.Xml.Serialization.XmlSchemaImporter> třídy.</span><span class="sxs-lookup"><span data-stu-id="57f56-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

## <a name="related-sections"></a><span data-ttu-id="57f56-149">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="57f56-149">Related Sections</span></span>

<span data-ttu-id="57f56-150">[Webové služby XML vytvořené pomocí ASP.NET a klienty webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="57f56-150">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>  
<span data-ttu-id="57f56-151">Obsahuje témata, které popisují a vysvětluje, jak program webové služby XML pomocí technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="57f56-151">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="57f56-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57f56-152">See also</span></span>

- [<span data-ttu-id="57f56-153">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="57f56-153">Binary Serialization</span></span>](binary-serialization.md)
