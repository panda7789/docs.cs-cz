---
title: "Serializace nástroje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593b675f-938c-44ff-807b-0ca9fea30103
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33da3336cc78763de080eb21e3b84fd4cfdc7716
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="serialization-tools"></a><span data-ttu-id="59be3-102">Serializace nástroje</span><span class="sxs-lookup"><span data-stu-id="59be3-102">Serialization Tools</span></span>
<span data-ttu-id="59be3-103">Tento oddíl obsahuje podrobné informace o nástrojích pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="59be3-103">This section contains detailed information about the serialization tools.</span></span> <span data-ttu-id="59be3-104">Všechny nástroje můžete spustit z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="59be3-104">You can run all the tools from the command line.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59be3-105">Pro rozhraní .NET Framework nástroje fungovat správně je nutné nastavit cestu, zahrnutí a Lib proměnné prostředí správně.</span><span class="sxs-lookup"><span data-stu-id="59be3-105">For the .NET Framework tools to function properly, you must set your Path, Include, and Lib environment variables correctly.</span></span> <span data-ttu-id="59be3-106">Nastavení těchto proměnných prostředí spuštěním SDKVars.bat, který je umístěný ve \<SDK > \v2.0\Bin adresáře.</span><span class="sxs-lookup"><span data-stu-id="59be3-106">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\v2.0\Bin directory.</span></span> <span data-ttu-id="59be3-107">SDKVars.bat je třeba spustit v každém příkazovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="59be3-107">SDKVars.bat must be executed in every command shell.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59be3-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="59be3-108">In This Section</span></span>  
  
|<span data-ttu-id="59be3-109">Nástroj</span><span class="sxs-lookup"><span data-stu-id="59be3-109">Tool</span></span>|<span data-ttu-id="59be3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="59be3-110">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="59be3-111">Nástroj XML Serializer Generator (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="59be3-111">XML Serializer Generator Tool (Sgen.exe)</span></span>](../../../docs/standard/serialization/xml-serializer-generator-tool-sgen-exe.md)|<span data-ttu-id="59be3-112">Vytvoří sestavení serializace XML pro typy v zadané sestavení s cílem zlepšit výkon běhu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="59be3-112">Creates an XML serialization assembly for types in a specified assembly in order to improve the run-time performance of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="59be3-113">Nástroj XML Schema Definition (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="59be3-113">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)|<span data-ttu-id="59be3-114">Generuje schémat XML, které následují jazyk XSD navrhovaná World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="59be3-114">Generates XML schemas that follow the XSD language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="59be3-115">Tento nástroj generuje běžné třídy language runtime a <xref:System.Data.DataSet> třídy ze souboru schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="59be3-115">This tool generates common language runtime classes and <xref:System.Data.DataSet> classes from an XSD schema file.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59be3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="59be3-116">See Also</span></span>  
 [<span data-ttu-id="59be3-117">Nástroje</span><span class="sxs-lookup"><span data-stu-id="59be3-117">Tools</span></span>](../../../docs/framework/tools/index.md)
