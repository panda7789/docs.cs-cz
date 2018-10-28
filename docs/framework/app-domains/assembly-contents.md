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
ms.openlocfilehash: 1aed7e1e9e85f746c4b55b10c59dd82e85565b00
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194836"
---
# <a name="assembly-contents"></a><span data-ttu-id="9b034-102">Obsah sestavení</span><span class="sxs-lookup"><span data-stu-id="9b034-102">Assembly Contents</span></span>
<span data-ttu-id="9b034-103">Obecně platí Statická sestavení se může skládat z čtyři elementy:</span><span class="sxs-lookup"><span data-stu-id="9b034-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="9b034-104">[Manifestu sestavení](../../../docs/framework/app-domains/assembly-manifest.md), který obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b034-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="9b034-105">Typ metadat.</span><span class="sxs-lookup"><span data-stu-id="9b034-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="9b034-106">Microsoft intermediate language (MSIL) kód, který implementuje typy.</span><span class="sxs-lookup"><span data-stu-id="9b034-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="9b034-107">Sada prostředků.</span><span class="sxs-lookup"><span data-stu-id="9b034-107">A set of resources.</span></span>  
  
 <span data-ttu-id="9b034-108">Vyžaduje se jenom manifest sestavení, ale typy nebo prostředky je nutné poskytnout sestavení žádné smysluplné funkce.</span><span class="sxs-lookup"><span data-stu-id="9b034-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="9b034-109">Existuje několik způsobů seskupení těchto prvků v sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b034-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="9b034-110">Můžete seskupit všechny prvky v jednom fyzickém souboru, která je znázorněna na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="9b034-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 <span data-ttu-id="9b034-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span><span class="sxs-lookup"><span data-stu-id="9b034-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span></span>  
<span data-ttu-id="9b034-112">Jeden soubor sestavení</span><span class="sxs-lookup"><span data-stu-id="9b034-112">Single-file assembly</span></span>  
  
 <span data-ttu-id="9b034-113">Alternativně prvky sestavení mohou být obsaženy v několika souborů.</span><span class="sxs-lookup"><span data-stu-id="9b034-113">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="9b034-114">Tyto soubory mohou být moduly zkompilovaného kódu (.netmodule), prostředky (například soubory .bmp nebo .jpg) nebo jiné soubory vyžadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="9b034-114">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="9b034-115">Pokud chcete kombinovat modulů napsaných v různých jazycích tak, že aplikace tak, že vložíte zřídka použít typy v modulu, který se stáhne jenom v případě potřeby vytvořte vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b034-115">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="9b034-116">Na následujícím obrázku vývojář aplikace hypotetické zvolil oddělit nějaký kód nástroje do jiného modulu a zachovat velkého souboru prostředků (v tomto případě obrázek bmp) v původním souboru.</span><span class="sxs-lookup"><span data-stu-id="9b034-116">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="9b034-117">Rozhraní .NET Framework stáhne soubor pouze v případě, že se na ni odkazuje; udržování kódu zřídka odkazované v samostatném souboru z aplikace optimalizuje kód ke stažení.</span><span class="sxs-lookup"><span data-stu-id="9b034-117">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 <span data-ttu-id="9b034-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span><span class="sxs-lookup"><span data-stu-id="9b034-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span></span>  
<span data-ttu-id="9b034-119">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="9b034-119">Multifile assembly</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b034-120">Soubory, které tvoří vícesouborového sestavení nejsou fyzicky připojeny systémem souborů.</span><span class="sxs-lookup"><span data-stu-id="9b034-120">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="9b034-121">Místo toho jsou propojeny prostřednictvím manifest sestavení a modul common language runtime spravuje jako celek.</span><span class="sxs-lookup"><span data-stu-id="9b034-121">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="9b034-122">Na tomto obrázku všechny tři soubory patří do sestavení, jak je popsáno v manifestu sestavení součástí MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="9b034-122">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="9b034-123">Jsou tři samostatné soubory do systému souborů.</span><span class="sxs-lookup"><span data-stu-id="9b034-123">To the file system, they are three separate files.</span></span> <span data-ttu-id="9b034-124">Soubor Util.netmodule byl zkompilován jako modul, protože neobsahuje žádné informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b034-124">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="9b034-125">Při vytváření sestavení byl manifest sestavení přidán do knihovny MyAssembly.dll, čímž je naznačen vztah se soubory Util.netmodule a Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="9b034-125">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="9b034-126">Při návrhu aktuálně zdrojového kódu, proveďte explicitní rozhodnutí o tom, jak rozdělit funkce vaší aplikace do jednoho nebo více souborů.</span><span class="sxs-lookup"><span data-stu-id="9b034-126">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="9b034-127">Při navrhování kódu rozhraní .NET Framework, bude podobné rozhodnutí o tom, jak rozdělit funkce do jednoho nebo více sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b034-127">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b034-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b034-128">See Also</span></span>  
- [<span data-ttu-id="9b034-129">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="9b034-129">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [<span data-ttu-id="9b034-130">Manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="9b034-130">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)  
- [<span data-ttu-id="9b034-131">Důležité informace o zabezpečení sestavení</span><span class="sxs-lookup"><span data-stu-id="9b034-131">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
