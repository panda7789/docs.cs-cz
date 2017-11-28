---
title: "Vlastní serializace pořadí pomocí třídy XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 16032a7df2df374d6201f8da18d563deceeeb5bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="7b1e2-102">Vlastní serializace pořadí pomocí třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="7b1e2-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="7b1e2-103">Stažení ukázky</span><span class="sxs-lookup"><span data-stu-id="7b1e2-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="7b1e2-104">Tento příklad ukazuje, jak lze řídit pořadí elementů serializované a deserializovat pro serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="7b1e2-105">Komentáře v souborech zdrojového kódu a build.proj Další informace o serializaci.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="7b1e2-106">K vytvoření vzorku pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7b1e2-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="7b1e2-107">Otevřete okno příkazového řádku a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="7b1e2-108">Typ **msbuild CustomOrder.sln** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="7b1e2-109">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7b1e2-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="7b1e2-110">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="7b1e2-111">Poklepejte na ikonu CustomOrder.sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="7b1e2-112">V **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="7b1e2-113">Vzorová aplikace je sestavena v podadresáři \bin nebo \bin\Debug výchozí.</span><span class="sxs-lookup"><span data-stu-id="7b1e2-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1e2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b1e2-114">See Also</span></span>  
 [<span data-ttu-id="7b1e2-115">Základní serializace</span><span class="sxs-lookup"><span data-stu-id="7b1e2-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="7b1e2-116">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="7b1e2-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="7b1e2-117">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="7b1e2-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="7b1e2-118">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="7b1e2-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="7b1e2-119">Serializace</span><span class="sxs-lookup"><span data-stu-id="7b1e2-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="7b1e2-120">XML a serializace protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="7b1e2-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
