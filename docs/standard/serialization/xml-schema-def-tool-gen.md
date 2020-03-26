---
title: 'Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 4c6996e2279693cf96c826741869d72007cf81cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249549"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="a34c2-102">Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition</span><span class="sxs-lookup"><span data-stu-id="a34c2-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="a34c2-103">Nástroj definici schématu XML (Xsd.exe) slouží ke generování schématu XML, která popisuje třídu nebo ke generování třídy definované ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="a34c2-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="a34c2-104">Následující postupy ukazují, jak provádět tyto operace.</span><span class="sxs-lookup"><span data-stu-id="a34c2-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="a34c2-105">Chcete-li generovat třídy, které odpovídají určité schéma</span><span class="sxs-lookup"><span data-stu-id="a34c2-105">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="a34c2-106">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="a34c2-106">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="a34c2-107">Předejte schématu XML jako argument nástroj definici schématu XML, který vytvoří sadu tříd, které budou přesně odpovídat schématu XML, například:</span><span class="sxs-lookup"><span data-stu-id="a34c2-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="a34c2-108">Nástroj lze zpracovat pouze schémata, které odkazují na specifikaci World Wide Web Consortium XML ze dne 16.</span><span class="sxs-lookup"><span data-stu-id="a34c2-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="a34c2-109">Jinými slovy, obor názvů schématu XMLhttp://www.w3.org/2001/XMLSchemamusí být " " jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a34c2-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="a34c2-110">Upravte tříd pomocí metody, vlastnosti nebo pole, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a34c2-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="a34c2-111">Další informace o úpravách třídy s atributy naleznete v [tématu Řízení serializace XML pomocí atributů](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) a [atributů, které řídí kódovnou serializaci SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="a34c2-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="a34c2-112">Často je užitečné si prohlédnout schématu XML datový proud, který je generována, když jsou serializovat instance třídy (nebo třídy).</span><span class="sxs-lookup"><span data-stu-id="a34c2-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="a34c2-113">Například může publikovat vaše schéma ostatním uživatelům, nebo vám může porovnat s schématu, ke které se snaží dosáhnout shody.</span><span class="sxs-lookup"><span data-stu-id="a34c2-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="a34c2-114">Generovat dokument XML schématu ze sady tříd</span><span class="sxs-lookup"><span data-stu-id="a34c2-114">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="a34c2-115">Zkompilujte třídu nebo třídy do knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="a34c2-115">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="a34c2-116">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="a34c2-116">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="a34c2-117">Předejte knihovny DLL jako argument Xsd.exe, například:</span><span class="sxs-lookup"><span data-stu-id="a34c2-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="a34c2-118">Schéma (nebo schémata), bude napsán, počínaje název "schema0.xsd".</span><span class="sxs-lookup"><span data-stu-id="a34c2-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a34c2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a34c2-119">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="a34c2-120">Nástroj definice schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="a34c2-120">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="a34c2-121">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="a34c2-121">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="a34c2-122">Nástroje definice schématu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="a34c2-122">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="a34c2-123">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="a34c2-123">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="a34c2-124">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="a34c2-124">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
