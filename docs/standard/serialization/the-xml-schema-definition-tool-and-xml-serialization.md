---
title: Nástroj definice schématu XML a serializace XML
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: b51b9a0112893d9a7838155f4af051e7079c8cdd
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588391"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="b4290-102">Nástroj definice schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="b4290-102">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="b4290-103">Nástroj Definice schématu XML ([Nástroj pro definici schématu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) je nainstalován společně&reg; s nástroji rozhraní .NET Framework jako součást sady Windows Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="b4290-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="b4290-104">Nástroj je určen především ke dvěma účelům:</span><span class="sxs-lookup"><span data-stu-id="b4290-104">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="b4290-105">Chcete-li generovat buď C# nebo Visual Basic souborů třídy, které odpovídají konkrétní jazyk (XSD) schématu definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="b4290-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="b4290-106">Nástroj přebírá schématu XML jako argument a uloží soubor, který obsahuje mnoho třída, která je, když serializované pomocí <xref:System.Xml.Serialization.XmlSerializer>, odpovídat schématu.</span><span class="sxs-lookup"><span data-stu-id="b4290-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="b4290-107">Informace o použití nástroje ke generování tříd, které odpovídají určitému schématu, naleznete v [tématu Postup: Pomocí nástroje definice schématu XML vygenerujte třídy a dokumenty schématu XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="b4290-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="b4290-108">Generovat dokument schématu XML ze souboru .dll nebo .exe souboru.</span><span class="sxs-lookup"><span data-stu-id="b4290-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="b4290-109">Chcete-li zobrazit schéma sadu souborů, které máte vytvořen nebo ten, který byl upraven, s atributy, předejte knihovna DLL nebo EXE jako argument nástroj pro generování schématu XML.</span><span class="sxs-lookup"><span data-stu-id="b4290-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="b4290-110">Informace o použití nástroje ke generování dokumentu schématu XML ze sady tříd naleznete v tématu [Postup: Pomocí nástroje definice schématu XML vygenerujte třídy a dokumenty schématu XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="b4290-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="b4290-111">Další informace o použití nástroje naleznete v tématu [Xml Schema Definition Tool (Xsd.exe).](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)</span><span class="sxs-lookup"><span data-stu-id="b4290-111">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4290-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4290-112">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="b4290-113">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="b4290-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="b4290-114">Nástroje definice schématu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="b4290-114">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="b4290-115">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="b4290-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="b4290-116">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="b4290-116">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="b4290-117">Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition</span><span class="sxs-lookup"><span data-stu-id="b4290-117">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="b4290-118">[Podpora vazby schématu XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b4290-118">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
