---
title: Nástroj definice schématu XML a serializace XML
description: Nástroj definice schématu XML generuje soubory tříd jazyka C# nebo Visual Basic pro schéma XSD a generuje schéma XML z knihovny nebo spustitelného souboru.
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 258e66643dae64aec7280419911f5ac9193a2ada
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380107"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="d1467-103">Nástroj definice schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="d1467-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="d1467-104">Nástroj definice schématu XML ([XSD. exe) (XML Schema Definition Tool](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) je nainstalován společně s nástroji pro .NET Framework jako součást sady Windows &reg; Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="d1467-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="d1467-105">Nástroj je určen především ke dvěma účelům:</span><span class="sxs-lookup"><span data-stu-id="d1467-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="d1467-106">Chcete-li generovat buď C# nebo Visual Basic souborů třídy, které odpovídají konkrétní jazyk (XSD) schématu definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d1467-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="d1467-107">Nástroj přebírá schématu XML jako argument a uloží soubor, který obsahuje mnoho třída, která je, když serializované pomocí <xref:System.Xml.Serialization.XmlSerializer>, odpovídat schématu.</span><span class="sxs-lookup"><span data-stu-id="d1467-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="d1467-108">Informace o tom, jak pomocí nástroje generovat třídy, které odpovídají konkrétnímu schématu, naleznete v tématu [How to: Use a XML Schema Definition Tool ke generování tříd a dokumentů schémat XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="d1467-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="d1467-109">Generovat dokument schématu XML ze souboru .dll nebo .exe souboru.</span><span class="sxs-lookup"><span data-stu-id="d1467-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="d1467-110">Chcete-li zobrazit schéma sadu souborů, které máte vytvořen nebo ten, který byl upraven, s atributy, předejte knihovna DLL nebo EXE jako argument nástroj pro generování schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d1467-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="d1467-111">Informace o použití nástroje ke generování dokumentu schématu XML ze sady tříd naleznete v tématu [How to: Use a XML Schema Definition Tool ke generování tříd a dokumentů schémat XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="d1467-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="d1467-112">Další informace o použití tohoto nástroje naleznete v tématu [Nástroj definice schématu XML (XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d1467-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1467-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1467-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="d1467-114">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="d1467-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="d1467-115">Nástroj definice schématu XML (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="d1467-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="d1467-116">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="d1467-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="d1467-117">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="d1467-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="d1467-118">Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition</span><span class="sxs-lookup"><span data-stu-id="d1467-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="d1467-119">[Podpora vazeb schématu XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1467-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
