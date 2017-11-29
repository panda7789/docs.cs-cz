---
title: "Obsah sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b51380126de164a4e0934068c7e0de55f5f3d92e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-contents"></a><span data-ttu-id="d5ed3-102">Obsah sestavení</span><span class="sxs-lookup"><span data-stu-id="d5ed3-102">Assembly Contents</span></span>
<span data-ttu-id="d5ed3-103">Obecně platí statické sestavení se může skládat ze čtyř prvků:</span><span class="sxs-lookup"><span data-stu-id="d5ed3-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="d5ed3-104">[Manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md), který obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="d5ed3-105">Metadata typu.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="d5ed3-106">Microsoft (MSIL intermediate language) kód, který implementuje typy.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="d5ed3-107">Sadu prostředků.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-107">A set of resources.</span></span>  
  
 <span data-ttu-id="d5ed3-108">Manifest sestavení není požadována, ale buď typy nebo prostředky je nutné poskytnout sestavení žádné smysluplný funkce.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="d5ed3-109">Existuje několik způsobů, jak seskupit tyto prvky v sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="d5ed3-110">Můžete seskupit všechny elementy do jednoho fyzického souboru, který je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 <span data-ttu-id="d5ed3-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span><span class="sxs-lookup"><span data-stu-id="d5ed3-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span></span>  
<span data-ttu-id="d5ed3-112">Jeden soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="d5ed3-112">Single-file assembly</span></span>  
  
 <span data-ttu-id="d5ed3-113">Alternativně elementy sestavení může obsahovat několik souborů.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-113">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="d5ed3-114">Tyto soubory mohou být moduly zkompilovaného kódu (.netmodule), prostředky (například soubory .bmp nebo .jpg) nebo jiné soubory vyžadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-114">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="d5ed3-115">Vytváření vícesouborového sestavení, pokud chcete kombinovat moduly, které jsou napsané v různých jazycích tak, že aplikace umístěním málokdy použít typy v modulu, který byl stažen pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-115">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="d5ed3-116">Na následujícím obrázku má vývojář hypotetické aplikace vybrali oddělení některé nástroj kódu do jiného modulu a udržování velkého souboru prostředků (v tomto případě bitovou kopii .bmp) v jeho původní soubor.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-116">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="d5ed3-117">Rozhraní .NET Framework stáhne soubor jenom v případě, že je odkazován; udržování zřídka odkazovaného kódu v samostatném souboru z aplikace optimalizuje stahování kódu.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-117">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 <span data-ttu-id="d5ed3-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span><span class="sxs-lookup"><span data-stu-id="d5ed3-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span></span>  
<span data-ttu-id="d5ed3-119">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="d5ed3-119">Multifile assembly</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5ed3-120">Soubory, které tvoří vícesouborového sestavení nejsou propojeny fyzicky prostřednictvím systému souborů.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-120">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="d5ed3-121">Místo toho jsou propojeny prostřednictvím manifestu sestavení a modul common language runtime je spravuje jako jednotku.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-121">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="d5ed3-122">V tomto obrázku všechny tři soubory patří sestavení, jak je popsáno v manifestu sestavení součástí MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-122">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="d5ed3-123">K systému souborů jsou tři samostatné soubory.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-123">To the file system, they are three separate files.</span></span> <span data-ttu-id="d5ed3-124">Soubor Util.netmodule byl zkompilován jako modul, protože neobsahuje žádné informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-124">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="d5ed3-125">Při vytváření sestavení byl manifest sestavení přidán do knihovny MyAssembly.dll, čímž je naznačen vztah se soubory Util.netmodule a Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-125">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="d5ed3-126">Při navrhování aktuálně vašeho zdrojového kódu, provedete explicitní rozhodnutí o tom, jak oddílu funkci vaší aplikace do jednoho nebo více souborů.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-126">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="d5ed3-127">Při navrhování kódu rozhraní .NET Framework, budou podobné rozhodnutí o tom, jak oddílu funkce do jednoho nebo více sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5ed3-127">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ed3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5ed3-128">See Also</span></span>  
 [<span data-ttu-id="d5ed3-129">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="d5ed3-129">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="d5ed3-130">Manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="d5ed3-130">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)  
 [<span data-ttu-id="d5ed3-131">Důležité informace o zabezpečení sestavení</span><span class="sxs-lookup"><span data-stu-id="d5ed3-131">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
