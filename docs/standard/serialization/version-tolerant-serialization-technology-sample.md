---
title: Ukázka technologie serializace tolerantní vůči verzím
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 6c30c39848be02785b6b808ecf4af711c0c9e95d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66482992"
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="85b8b-102">Ukázka technologie serializace tolerantní vůči verzím</span><span class="sxs-lookup"><span data-stu-id="85b8b-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="85b8b-103">Stáhněte si ukázky</span><span class="sxs-lookup"><span data-stu-id="85b8b-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="85b8b-104">Tento příklad znázorňuje verze funkce tolerance serializace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="85b8b-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="85b8b-105">Ukázka sestavení aplikace, které používají různé verze <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> k serializaci a deserializaci data.</span><span class="sxs-lookup"><span data-stu-id="85b8b-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="85b8b-106">Bez ohledu na přítomnost jiný typ verze aplikace komunikovat bez problémů.</span><span class="sxs-lookup"><span data-stu-id="85b8b-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="85b8b-107">Další informace najdete v tématu [serializace tolerantní vůči verzím verze](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="85b8b-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="85b8b-108">K vytvoření vzorku pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="85b8b-108">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="85b8b-109">Otevřete okno příkazového řádku a přejděte do jednoho podadresáře konkrétní jazyk (v rámci aplikace V1 nebo V2 aplikace) pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="85b8b-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2. <span data-ttu-id="85b8b-110">Typ **msbuild.exe \<verů > application.sln** příkazového řádku (kde \<verů > je v1 nebo v2).</span><span class="sxs-lookup"><span data-stu-id="85b8b-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="85b8b-111">K vytvoření vzorku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="85b8b-111">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="85b8b-112">Otevřete Průzkumníka souborů a přejděte do jednoho podadresáře konkrétní jazyk pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="85b8b-112">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="85b8b-113">Přejděte do aplikace V1 podadresáře adresáře, který jste vybrali v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="85b8b-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3. <span data-ttu-id="85b8b-114">Poklepejte na ikonu V1 Application.sln k otevření souboru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85b8b-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4. <span data-ttu-id="85b8b-115">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="85b8b-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5. <span data-ttu-id="85b8b-116">Přejděte do podadresáře V2 aplikace a opakujte předchozí dva kroky pro vytvoření aplikace V2.</span><span class="sxs-lookup"><span data-stu-id="85b8b-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="85b8b-117">Aplikace bude vytvořen v výchozí \bin nebo \bin\Debug podadresářích adresáře jejich příslušného projektu.</span><span class="sxs-lookup"><span data-stu-id="85b8b-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="85b8b-118">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="85b8b-118">To run the sample</span></span>  
  
1. <span data-ttu-id="85b8b-119">V okně příkazového řádku přejděte na konkrétní jazyk podadresář, který jste vybrali, když jste vytvořili ukázkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="85b8b-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2. <span data-ttu-id="85b8b-120">Typ **runme.cmd** na příkazovém řádku spusťte obě aplikace najednou.</span><span class="sxs-lookup"><span data-stu-id="85b8b-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="85b8b-121">Alternativně přejděte do adresáře, které obsahují nové spustitelné soubory a spustit je postupně.</span><span class="sxs-lookup"><span data-stu-id="85b8b-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85b8b-122">Ukázka sestavení aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="85b8b-122">The sample builds console applications.</span></span> <span data-ttu-id="85b8b-123">Je nutné spustit a spustit v okně příkazového řádku, chcete-li zobrazit jejich výstup.</span><span class="sxs-lookup"><span data-stu-id="85b8b-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b8b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85b8b-124">See also</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
