---
title: Vlastní serializace pořadí pomocí třídy XmlSerializer
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b091d07ada0031013c935c5ab12b77ebedd6bcc3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="fe99b-102">Vlastní serializace pořadí pomocí třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="fe99b-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="fe99b-103">Stažení ukázky</span><span class="sxs-lookup"><span data-stu-id="fe99b-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="fe99b-104">Tento příklad ukazuje, jak lze řídit pořadí elementů serializované a deserializovat pro serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="fe99b-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="fe99b-105">Komentáře v souborech zdrojového kódu a build.proj Další informace o serializaci.</span><span class="sxs-lookup"><span data-stu-id="fe99b-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="fe99b-106">K vytvoření vzorku pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="fe99b-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="fe99b-107">Otevřete okno příkazového řádku a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="fe99b-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="fe99b-108">Typ **msbuild CustomOrder.sln** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="fe99b-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="fe99b-109">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fe99b-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="fe99b-110">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="fe99b-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="fe99b-111">Poklepejte na ikonu CustomOrder.sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe99b-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="fe99b-112">V **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="fe99b-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="fe99b-113">Vzorová aplikace je sestavena v podadresáři \bin nebo \bin\Debug výchozí.</span><span class="sxs-lookup"><span data-stu-id="fe99b-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe99b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe99b-114">See Also</span></span>  
 [<span data-ttu-id="fe99b-115">Základní serializace</span><span class="sxs-lookup"><span data-stu-id="fe99b-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="fe99b-116">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="fe99b-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="fe99b-117">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="fe99b-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="fe99b-118">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="fe99b-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="fe99b-119">Serializace</span><span class="sxs-lookup"><span data-stu-id="fe99b-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="fe99b-120">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="fe99b-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
