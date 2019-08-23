---
title: Obsah sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1334f8c8e1b5898e93697461f609429d4aae764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921706"
---
# <a name="assembly-contents"></a><span data-ttu-id="6ead3-102">Obsah sestavení</span><span class="sxs-lookup"><span data-stu-id="6ead3-102">Assembly Contents</span></span>
<span data-ttu-id="6ead3-103">Obecně platí, že statické sestavení se může skládat ze čtyř prvků:</span><span class="sxs-lookup"><span data-stu-id="6ead3-103">In general, a static assembly can consist of four elements:</span></span>  
  
- <span data-ttu-id="6ead3-104">[Manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md), který obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ead3-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
- <span data-ttu-id="6ead3-105">Zadejte metadata.</span><span class="sxs-lookup"><span data-stu-id="6ead3-105">Type metadata.</span></span>  
  
- <span data-ttu-id="6ead3-106">Kód jazyka MSIL (Microsoft Intermediate Language), který implementuje typy.</span><span class="sxs-lookup"><span data-stu-id="6ead3-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
- <span data-ttu-id="6ead3-107">Sada prostředků.</span><span class="sxs-lookup"><span data-stu-id="6ead3-107">A set of resources.</span></span>  
  
 <span data-ttu-id="6ead3-108">Vyžaduje se pouze manifest sestavení, ale k sestavení všech smysluplných funkcí je nutné zadat buď typy, nebo prostředky.</span><span class="sxs-lookup"><span data-stu-id="6ead3-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="6ead3-109">Existuje několik způsobů, jak seskupit tyto prvky do sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ead3-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="6ead3-110">Všechny prvky můžete seskupit v jednom fyzickém souboru, který je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="6ead3-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 ![Diagram, který zobrazuje sestavení s jedním souborem s názvem MyAssembly. dll.](./media/assembly-contents/single-file-assembly.gif)  
  
 <span data-ttu-id="6ead3-112">Alternativně mohou být prvky sestavení obsaženy v několika souborech.</span><span class="sxs-lookup"><span data-stu-id="6ead3-112">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="6ead3-113">Tyto soubory mohou být moduly zkompilovaného kódu (.netmodule), prostředky (například soubory .bmp nebo .jpg) nebo jiné soubory vyžadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="6ead3-113">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="6ead3-114">Vytvořte vícesouborové sestavení, pokud chcete kombinovat moduly napsané v různých jazycích a optimalizovat stahování aplikace tím, že zadáte zřídka používané typy v modulu, který se stáhne pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="6ead3-114">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="6ead3-115">Na následujícím obrázku se vývojář hypotetické aplikace rozhodl oddělit některé kódy nástrojů do jiného modulu a uchovávat velký soubor prostředků (v tomto případě obrázek. bmp) v původním souboru.</span><span class="sxs-lookup"><span data-stu-id="6ead3-115">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="6ead3-116">.NET Framework stáhne soubor pouze v případě, že je odkazováno. udržování zřídka odkazovaného kódu v samostatném souboru z aplikace optimalizuje stahování kódu.</span><span class="sxs-lookup"><span data-stu-id="6ead3-116">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 ![Diagram, který zobrazuje vícesouborové sestavení.](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
> <span data-ttu-id="6ead3-118">Soubory, které tvoří vícesouborové sestavení, nejsou fyzicky propojeny systémem souborů.</span><span class="sxs-lookup"><span data-stu-id="6ead3-118">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="6ead3-119">Místo toho jsou propojeny prostřednictvím manifestu sestavení a modul CLR (Common Language Runtime) je spravuje jako celek.</span><span class="sxs-lookup"><span data-stu-id="6ead3-119">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="6ead3-120">Na tomto obrázku všechny tři soubory patří do sestavení, jak je popsáno v manifestu sestavení obsaženém v MyAssembly. dll.</span><span class="sxs-lookup"><span data-stu-id="6ead3-120">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="6ead3-121">Do systému souborů jsou tři samostatné soubory.</span><span class="sxs-lookup"><span data-stu-id="6ead3-121">To the file system, they are three separate files.</span></span> <span data-ttu-id="6ead3-122">Soubor Util.netmodule byl zkompilován jako modul, protože neobsahuje žádné informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ead3-122">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="6ead3-123">Při vytváření sestavení byl manifest sestavení přidán do knihovny MyAssembly.dll, čímž je naznačen vztah se soubory Util.netmodule a Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="6ead3-123">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="6ead3-124">Při navrhování zdrojového kódu se při rozhodování o tom, jak rozdělit funkce aplikace do jednoho nebo více souborů, provést explicitní rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="6ead3-124">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="6ead3-125">Při navrhování .NET Framework kódu provedete podobná rozhodnutí týkající se dělení funkcí do jednoho nebo více sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ead3-125">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ead3-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ead3-126">See also</span></span>

- [<span data-ttu-id="6ead3-127">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="6ead3-127">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="6ead3-128">Manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="6ead3-128">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="6ead3-129">Důležité informace o zabezpečení sestavení</span><span class="sxs-lookup"><span data-stu-id="6ead3-129">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
