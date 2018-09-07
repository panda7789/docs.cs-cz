---
title: Vlastní pořadí serializace pomocí třídy XmlSerializer
ms.date: 03/30/2017
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
ms.openlocfilehash: 1dc9a73b45d8e62902ec8c6b7d810154a8a92566
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071944"
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="c4a1e-102">Vlastní pořadí serializace pomocí třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="c4a1e-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="c4a1e-103">Stáhněte si ukázky</span><span class="sxs-lookup"><span data-stu-id="c4a1e-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="c4a1e-104">Tento příklad ukazuje, jak lze řídit pořadí elementů serializované a deserializovat pro serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="c4a1e-105">Komentáře v souborech zdrojového kódu a build.proj Další informace o serializaci.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="c4a1e-106">K vytvoření vzorku pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c4a1e-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="c4a1e-107">Otevřete okno příkazového řádku a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="c4a1e-108">Typ **msbuild CustomOrder.sln** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="c4a1e-109">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4a1e-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="c4a1e-110">Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="c4a1e-111">Poklepejte na ikonu CustomOrder.sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="c4a1e-112">V **sestavení** nabídce vyberte možnost **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="c4a1e-113">Vzorová aplikace je sestavena v podadresáři \bin nebo \bin\Debug výchozí.</span><span class="sxs-lookup"><span data-stu-id="c4a1e-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a1e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4a1e-114">See also</span></span>

- [<span data-ttu-id="c4a1e-115">Základní serializace</span><span class="sxs-lookup"><span data-stu-id="c4a1e-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
- [<span data-ttu-id="c4a1e-116">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="c4a1e-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
- [<span data-ttu-id="c4a1e-117">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="c4a1e-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [<span data-ttu-id="c4a1e-118">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="c4a1e-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [<span data-ttu-id="c4a1e-119">Serializace</span><span class="sxs-lookup"><span data-stu-id="c4a1e-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
- [<span data-ttu-id="c4a1e-120">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="c4a1e-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
