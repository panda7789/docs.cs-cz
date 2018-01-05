---
title: "Názvy sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da2137a9ab979d9e610d033324a87939a9777a97
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-names"></a><span data-ttu-id="191e5-102">Názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="191e5-102">Assembly Names</span></span>
<span data-ttu-id="191e5-103">Název sestavení je uložená v metadatech a má významný dopad na rozsah sestavení a používat jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="191e5-103">An assembly's name is stored in metadata and has a significant impact on the assembly's scope and use by an application.</span></span> <span data-ttu-id="191e5-104">Sestavení se silným názvem má plně kvalifikovaný název, který obsahuje název sestavení, jazykovou verzi, veřejný klíč a číslo verze.</span><span class="sxs-lookup"><span data-stu-id="191e5-104">A strong-named assembly has a fully qualified name that includes the assembly's name, culture, public key, and version number.</span></span> <span data-ttu-id="191e5-105">To se často označuje jako zobrazovaný název a pro načíst sestavení můžete získat pomocí <xref:System.Reflection.Assembly.FullName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="191e5-105">This is frequently referred to as the display name, and for loaded assemblies can be obtained by using the <xref:System.Reflection.Assembly.FullName%2A> property.</span></span>  
  
 <span data-ttu-id="191e5-106">Modul runtime používá tuto informaci k vyhledání sestavení a rozlišit ho od ostatních sestavení se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="191e5-106">The runtime uses this information to locate the assembly and differentiate it from other assemblies with the same name.</span></span> <span data-ttu-id="191e5-107">Například sestavení se silným názvem názvem `myTypes` může mít následující plně kvalifikovaný název:</span><span class="sxs-lookup"><span data-stu-id="191e5-107">For example, a strong-named assembly called `myTypes` could have the following fully qualified name:</span></span>  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  <span data-ttu-id="191e5-108">Architektura procesoru se přidá k identitě sestavení v rozhraní .NET Framework verze 2.0, aby specifické pro procesor verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="191e5-108">Processor architecture is added to the assembly identity in the .NET Framework version 2.0, to allow processor-specific versions of assemblies.</span></span> <span data-ttu-id="191e5-109">Můžete vytvořit verze sestavení, jehož identita se liší pouze pomocí architekturu procesoru, například verze specifické pro procesor 32bitové a 64bitové verze.</span><span class="sxs-lookup"><span data-stu-id="191e5-109">You can create versions of an assembly whose identity differs only by processor architecture, for example 32-bit and 64-bit processor-specific versions.</span></span> <span data-ttu-id="191e5-110">Architektura procesoru není nutné pro silné názvy.</span><span class="sxs-lookup"><span data-stu-id="191e5-110">Processor architecture is not required for strong names.</span></span> <span data-ttu-id="191e5-111">Další informace naleznete v tématu <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="191e5-111">For more information, see <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="191e5-112">V tomto příkladu plně kvalifikovaný název znamená, že `myTypes` sestavení se silným názvem pomocí tokenu veřejného klíče, má hodnota jazykové verze pro angličtinu a má číslo verze 1.0.1234.0.</span><span class="sxs-lookup"><span data-stu-id="191e5-112">In this example, the fully qualified name indicates that the `myTypes` assembly has a strong name with a public key token, has the culture value for US English, and has a version number of 1.0.1234.0.</span></span> <span data-ttu-id="191e5-113">Jeho architektura procesoru je "msil", což znamená, že bude v běhu (JIT)-zkompilovat kód 32bitový nebo 64bitový kód v závislosti na operačním systému a procesoru.</span><span class="sxs-lookup"><span data-stu-id="191e5-113">Its processor architecture is "msil", which means that it will be just-in-time (JIT)-compiled to 32-bit code or 64-bit code depending on the operating system and processor.</span></span>  
  
 <span data-ttu-id="191e5-114">Kód, který požaduje typy v sestavení musí použít plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="191e5-114">Code that requests types in an assembly must use a fully qualified assembly name.</span></span> <span data-ttu-id="191e5-115">Tomu se říká plně kvalifikovaný vazby.</span><span class="sxs-lookup"><span data-stu-id="191e5-115">This is called fully qualified binding.</span></span> <span data-ttu-id="191e5-116">Částečné vazby, která určuje jenom název sestavení, není povolena při odkazování na sestavení v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="191e5-116">Partial binding, which specifies only an assembly name, is not permitted when referencing assemblies in the .NET Framework.</span></span>  
  
 <span data-ttu-id="191e5-117">Všechny odkazy na sestavení pro sestavení, která tvoří rozhraní .NET Framework musí také obsahovat plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="191e5-117">All assembly references to assemblies that make up the .NET Framework also must contain a fully qualified name of the assembly.</span></span> <span data-ttu-id="191e5-118">Například k odkazování sestavení System.Data rozhraní .NET Framework pro verzi 1.0 by mělo zahrnovat:</span><span class="sxs-lookup"><span data-stu-id="191e5-118">For example, to reference the System.Data .NET Framework assembly for version 1.0 would include:</span></span>  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 <span data-ttu-id="191e5-119">Všimněte si, že verze odpovídá číslo verze všech sestavení rozhraní .NET Framework, která jsou součástí rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="191e5-119">Note that the version corresponds to the version number of all .NET Framework assemblies that shipped with .NET Framework version 1.0.</span></span> <span data-ttu-id="191e5-120">Pro sestavení rozhraní .NET Framework hodnota jazykové verze je vždy neutrální a veřejný klíč je stejný jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="191e5-120">For .NET Framework assemblies, the culture value is always neutral, and the public key is the same as shown in the above example.</span></span>  
  
 <span data-ttu-id="191e5-121">Pokud chcete přidat odkaz na sestavení v konfiguračním souboru nastavit naslouchací proces trasování, například bude zahrnovat plně kvalifikovaný název sestavení rozhraní .NET Framework systému:</span><span class="sxs-lookup"><span data-stu-id="191e5-121">For example, to add an assembly reference in a configuration file to set up a trace listener, you would include the fully qualified name of the system .NET Framework assembly:</span></span>  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  <span data-ttu-id="191e5-122">Modul runtime názvy sestavení považuje velká a malá písmena, při vytváření vazby k sestavení, ale zachová jakoukoli velikost písmen se používá v názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="191e5-122">The runtime treats assembly names as case-insensitive when binding to an assembly, but preserves whatever case is used in an assembly name.</span></span> <span data-ttu-id="191e5-123">Několik nástrojů v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] zpracování názvy sestavení jako malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="191e5-123">Several tools in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] handle assembly names as case-sensitive.</span></span> <span data-ttu-id="191e5-124">Nejlepších výsledků dosáhnete spravujte názvy sestavení, jako kdyby byly malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="191e5-124">For best results, manage assembly names as though they were case-sensitive.</span></span>  
  
## <a name="naming-application-components"></a><span data-ttu-id="191e5-125">Pojmenování součásti aplikace</span><span class="sxs-lookup"><span data-stu-id="191e5-125">Naming Application Components</span></span>  
 <span data-ttu-id="191e5-126">Modul runtime nebere v úvahu názvu souboru při určování identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="191e5-126">The runtime does not consider the file name when determining an assembly's identity.</span></span> <span data-ttu-id="191e5-127">Identita sestavení, která obsahuje název sestavení, verzi, jazykovou verzi a silným názvem, musí být jasná modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="191e5-127">The assembly identity, which consists of the assembly name, version, culture, and strong name, must be clear to the runtime.</span></span>  
  
 <span data-ttu-id="191e5-128">Například pokud máte sestavení nazvané myAssembly.exe, který odkazuje na sestavení nazvané myAssembly.dll, vazba dojde k správně Pokud spustíte myAssembly.exe.</span><span class="sxs-lookup"><span data-stu-id="191e5-128">For example, if you have an assembly called myAssembly.exe that references an assembly called myAssembly.dll, binding occurs correctly if you execute myAssembly.exe.</span></span> <span data-ttu-id="191e5-129">Ale pokud jiná aplikace spouští myAssembly.exe pomocí metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, modul runtime určuje, že "myAssembly" už je načtený, když myAssembly.exe žádá vazbu na "myAssembly."</span><span class="sxs-lookup"><span data-stu-id="191e5-129">However, if another application executes myAssembly.exe using the method <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, the runtime determines that "myAssembly" is already loaded when myAssembly.exe requests binding to "myAssembly."</span></span> <span data-ttu-id="191e5-130">V takovém případě myAssembly.dll nikdy načtena.</span><span class="sxs-lookup"><span data-stu-id="191e5-130">In this case, myAssembly.dll is never loaded.</span></span> <span data-ttu-id="191e5-131">Protože myAssembly.exe neobsahuje požadovaný typ <xref:System.TypeLoadException> dojde.</span><span class="sxs-lookup"><span data-stu-id="191e5-131">Because myAssembly.exe does not contain the requested type , a <xref:System.TypeLoadException> occurs.</span></span>  
  
 <span data-ttu-id="191e5-132">K tomuto problému nedošlo, zajistěte, aby, sestavení, které tvoří vaši aplikaci mají stejný název sestavení nebo sestavení se stejným názvem umístit do různých adresářů.</span><span class="sxs-lookup"><span data-stu-id="191e5-132">To avoid this problem, make sure the assemblies that make up your application do not have the same assembly name or place assemblies with the same name in different directories.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="191e5-133">Když vložíte sestavení se silným názvem v globální mezipaměti sestavení, název souboru sestavení musí odpovídat název sestavení (včetně není příponu názvu souboru, jako je například .exe nebo .dll).</span><span class="sxs-lookup"><span data-stu-id="191e5-133">If you put a strong-named assembly in the global assembly cache, the assembly's file name must match the assembly name (not including the file name extension, such as .exe or .dll).</span></span> <span data-ttu-id="191e5-134">Například pokud je název souboru sestavení myAssembly.dll, název sestavení musí být myAssembly.</span><span class="sxs-lookup"><span data-stu-id="191e5-134">For example, if the file name of an assembly is myAssembly.dll, the assembly name must be myAssembly.</span></span> <span data-ttu-id="191e5-135">Soukromá sestavení nasadit jenom v kořenovém adresáři aplikace může mít název sestavení, který se liší od názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="191e5-135">Private assemblies deployed only in the root application directory can have an assembly name that is different from the file name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191e5-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="191e5-136">See Also</span></span>  
 [<span data-ttu-id="191e5-137">Postupy: Určení plně kvalifikovaného názvu sestavení</span><span class="sxs-lookup"><span data-stu-id="191e5-137">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 [<span data-ttu-id="191e5-138">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="191e5-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="191e5-139">Sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="191e5-139">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [<span data-ttu-id="191e5-140">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="191e5-140">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="191e5-141">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="191e5-141">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="191e5-142">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="191e5-142">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
