---
title: "Nástroj definice schématu XML a serializace XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6bd462714ada242062c9e2e23f924868f5870ef8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="f7300-102">Nástroj definice schématu XML a serializace XML</span><span class="sxs-lookup"><span data-stu-id="f7300-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="f7300-103">Nástroje XML Schema Definition ([nástroje definice schématu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) je nainstalována spolu s nástroje rozhraní .NET Framework v rámci systému Windows® Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="f7300-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="f7300-104">Nástroj je určen především ke dvěma účelům:</span><span class="sxs-lookup"><span data-stu-id="f7300-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="f7300-105">Chcete-li generovat buď C# nebo Visual Basic souborů třídy, které odpovídají konkrétní jazyk (XSD) schématu definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f7300-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="f7300-106">Nástroj přebírá schématu XML jako argument a uloží soubor, který obsahuje mnoho třída, která je, když serializované pomocí <xref:System.Xml.Serialization.XmlSerializer>, odpovídat schématu.</span><span class="sxs-lookup"><span data-stu-id="f7300-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="f7300-107">Informace o tom, jak použít nástroj pro generování tříd, které odpovídají určité schéma najdete v tématu [postupy: použití nástroje definice schématu XML k generování tříd a dokumentech schémat XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="f7300-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="f7300-108">Generovat dokument schématu XML ze souboru .dll nebo .exe souboru.</span><span class="sxs-lookup"><span data-stu-id="f7300-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="f7300-109">Chcete-li zobrazit schéma sadu souborů, které máte vytvořen nebo ten, který byl upraven, s atributy, předejte knihovna DLL nebo EXE jako argument nástroj pro generování schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f7300-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="f7300-110">Informace o tom, jak použít nástroj ke generování dokument schématu XML z sadu tříd, najdete v tématu [postupy: použití nástroje definice schématu XML k generování tříd a dokumentech schémat XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="f7300-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="f7300-111">Další informace o tomto nástroji a ostatní najdete v tématu [nástroje](../../../docs/framework/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7300-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="f7300-112">Informace o možnostech nástroje najdete v tématu [nástroje definice schématu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f7300-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7300-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7300-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="f7300-114">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="f7300-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="f7300-115">Nástroje definice schématu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="f7300-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="f7300-116">Postupy: serializaci objektu</span><span class="sxs-lookup"><span data-stu-id="f7300-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="f7300-117">Postupy: deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="f7300-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="f7300-118">Postupy: použití nástroje definice schématu XML pro generování tříd a dokumentech schémat XML.</span><span class="sxs-lookup"><span data-stu-id="f7300-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="f7300-119">Schéma XML vazby podpora v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7300-119">XML Schema Binding Support in the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)
