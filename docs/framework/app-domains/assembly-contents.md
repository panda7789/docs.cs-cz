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
ms.openlocfilehash: 25594c55a5462c42611df7119dad37bd8a61cc2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705814"
---
# <a name="assembly-contents"></a><span data-ttu-id="a5fbb-102">Obsah sestavení</span><span class="sxs-lookup"><span data-stu-id="a5fbb-102">Assembly Contents</span></span>
<span data-ttu-id="a5fbb-103">Obecně platí Statická sestavení se může skládat z čtyři elementy:</span><span class="sxs-lookup"><span data-stu-id="a5fbb-103">In general, a static assembly can consist of four elements:</span></span>  
  
- <span data-ttu-id="a5fbb-104">[Manifestu sestavení](../../../docs/framework/app-domains/assembly-manifest.md), který obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
- <span data-ttu-id="a5fbb-105">Typ metadat.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-105">Type metadata.</span></span>  
  
- <span data-ttu-id="a5fbb-106">Microsoft intermediate language (MSIL) kód, který implementuje typy.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
- <span data-ttu-id="a5fbb-107">Sada prostředků.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-107">A set of resources.</span></span>  
  
 <span data-ttu-id="a5fbb-108">Vyžaduje se jenom manifest sestavení, ale typy nebo prostředky je nutné poskytnout sestavení žádné smysluplné funkce.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="a5fbb-109">Existuje několik způsobů seskupení těchto prvků v sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="a5fbb-110">Můžete seskupit všechny prvky v jednom fyzickém souboru, která je znázorněna na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 ![Diagram zobrazující průběh jednosouborového sestavení nazvané MyAssembly.dll.](./media/assembly-contents/single-file-assembly.gif)  
  
 <span data-ttu-id="a5fbb-112">Alternativně prvky sestavení mohou být obsaženy v několika souborů.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-112">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="a5fbb-113">Tyto soubory mohou být moduly zkompilovaného kódu (.netmodule), prostředky (například soubory .bmp nebo .jpg) nebo jiné soubory vyžadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-113">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="a5fbb-114">Pokud chcete kombinovat modulů napsaných v různých jazycích tak, že aplikace tak, že vložíte zřídka použít typy v modulu, který se stáhne jenom v případě potřeby vytvořte vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-114">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="a5fbb-115">Na následujícím obrázku vývojář aplikace hypotetické zvolil oddělit nějaký kód nástroje do jiného modulu a zachovat velkého souboru prostředků (v tomto případě obrázek bmp) v původním souboru.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-115">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="a5fbb-116">Rozhraní .NET Framework stáhne soubor pouze v případě, že se na ni odkazuje; udržování kódu zřídka odkazované v samostatném souboru z aplikace optimalizuje kód ke stažení.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-116">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 ![Diagram zobrazující průběh vícesouborové sestavení.](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
>  <span data-ttu-id="a5fbb-118">Soubory, které tvoří vícesouborového sestavení nejsou fyzicky připojeny systémem souborů.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-118">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="a5fbb-119">Místo toho jsou propojeny prostřednictvím manifest sestavení a modul common language runtime spravuje jako celek.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-119">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="a5fbb-120">Na tomto obrázku všechny tři soubory patří do sestavení, jak je popsáno v manifestu sestavení součástí MyAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-120">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="a5fbb-121">Jsou tři samostatné soubory do systému souborů.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-121">To the file system, they are three separate files.</span></span> <span data-ttu-id="a5fbb-122">Soubor Util.netmodule byl zkompilován jako modul, protože neobsahuje žádné informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-122">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="a5fbb-123">Při vytváření sestavení byl manifest sestavení přidán do knihovny MyAssembly.dll, čímž je naznačen vztah se soubory Util.netmodule a Graphic.bmp.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-123">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="a5fbb-124">Při návrhu aktuálně zdrojového kódu, proveďte explicitní rozhodnutí o tom, jak rozdělit funkce vaší aplikace do jednoho nebo více souborů.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-124">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="a5fbb-125">Při navrhování kódu rozhraní .NET Framework, bude podobné rozhodnutí o tom, jak rozdělit funkce do jednoho nebo více sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5fbb-125">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fbb-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5fbb-126">See also</span></span>

- [<span data-ttu-id="a5fbb-127">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="a5fbb-127">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="a5fbb-128">Manifest sestavení</span><span class="sxs-lookup"><span data-stu-id="a5fbb-128">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="a5fbb-129">Důležité informace o zabezpečení sestavení</span><span class="sxs-lookup"><span data-stu-id="a5fbb-129">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
