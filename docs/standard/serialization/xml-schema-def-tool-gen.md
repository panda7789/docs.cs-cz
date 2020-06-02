---
title: 'Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition'
description: Naučte se používat nástroj definice schématu XML ke generování schématu XML, který popisuje třídu nebo generuje třídu definovanou schématem XML.
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 0e4e84ea7e11b2e7a00c852d4a2075747c71267e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288963"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="ff7b7-103">Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition</span><span class="sxs-lookup"><span data-stu-id="ff7b7-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="ff7b7-104">Nástroj definici schématu XML (Xsd.exe) slouží ke generování schématu XML, která popisuje třídu nebo ke generování třídy definované ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="ff7b7-105">Následující postupy ukazují, jak provádět tyto operace.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="ff7b7-106">Nástroj pro definici schématu XML (XSD. exe) obvykle najdete v následující cestě: </span><span class="sxs-lookup"><span data-stu-id="ff7b7-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="ff7b7-107">_C: \\ Program Files (x86) \\ Microsoft SDK \\ Windows \\ {Version} \\ bin \\ netfx {Version} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="ff7b7-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="ff7b7-108">Chcete-li generovat třídy, které odpovídají určité schéma</span><span class="sxs-lookup"><span data-stu-id="ff7b7-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="ff7b7-109">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="ff7b7-110">Předejte schématu XML jako argument nástroj definici schématu XML, který vytvoří sadu tříd, které budou přesně odpovídat schématu XML, například:</span><span class="sxs-lookup"><span data-stu-id="ff7b7-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="ff7b7-111">Nástroj lze zpracovat pouze schémata, které odkazují na specifikaci World Wide Web Consortium XML ze dne 16.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="ff7b7-112">Jinými slovy obor názvů schématu XML musí být "", http://www.w3.org/2001/XMLSchema jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="ff7b7-113">Upravte tříd pomocí metody, vlastnosti nebo pole, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="ff7b7-114">Další informace o úpravách třídy s atributy naleznete v tématu [řízení serializace XML pomocí atributů](controlling-xml-serialization-using-attributes.md) a [atributů, které řídí serializaci kódovaných SOAP](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ff7b7-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="ff7b7-115">Často je užitečné si prohlédnout schématu XML datový proud, který je generována, když jsou serializovat instance třídy (nebo třídy).</span><span class="sxs-lookup"><span data-stu-id="ff7b7-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="ff7b7-116">Například může publikovat vaše schéma ostatním uživatelům, nebo vám může porovnat s schématu, ke které se snaží dosáhnout shody.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="ff7b7-117">Generovat dokument XML schématu ze sady tříd</span><span class="sxs-lookup"><span data-stu-id="ff7b7-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="ff7b7-118">Zkompilujte třídu nebo třídy do knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="ff7b7-119">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="ff7b7-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="ff7b7-120">Předejte knihovny DLL jako argument Xsd.exe, například:</span><span class="sxs-lookup"><span data-stu-id="ff7b7-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="ff7b7-121">Schéma (nebo schémata), bude napsán, počínaje název "schema0.xsd".</span><span class="sxs-lookup"><span data-stu-id="ff7b7-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff7b7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff7b7-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="ff7b7-123">Nástroj definice schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="ff7b7-123">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="ff7b7-124">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="ff7b7-124">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="ff7b7-125">Nástroj definice schématu XML (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="ff7b7-125">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="ff7b7-126">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="ff7b7-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="ff7b7-127">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="ff7b7-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
