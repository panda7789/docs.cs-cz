---
title: Oříznutí samostatných aplikací
description: Přečtěte si, jak oříznout samostatné aplikace, aby se zmenšila jejich velikost. .NET Core sdružuje runtime s aplikací, která je publikována samostatně a obecně obsahuje více runtime pak je nezbytné.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665633"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="30ec3-104">Oříznutí samostatných nasazení a spustitelných souborů</span><span class="sxs-lookup"><span data-stu-id="30ec3-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="30ec3-105">Při publikování samostatné aplikace je runtime .NET Core dodáván společně s aplikací.</span><span class="sxs-lookup"><span data-stu-id="30ec3-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="30ec3-106">Toto sdružování přidá značné množství obsahu do vaší balené aplikace.</span><span class="sxs-lookup"><span data-stu-id="30ec3-106">This bundling adds a significant amount of content to your packaged application.</span></span>

<span data-ttu-id="30ec3-107">Pokud jde o nasazení aplikace, velikost je často důležitým faktorem.</span><span class="sxs-lookup"><span data-stu-id="30ec3-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="30ec3-108">Zachování velikosti aplikace balíčku co nejmenší je obvykle cílem pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="30ec3-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="30ec3-109">V závislosti na složitosti aplikace je ke spuštění aplikace vyžadována pouze podmnožina runtime.</span><span class="sxs-lookup"><span data-stu-id="30ec3-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="30ec3-110">Tyto nepoužívané části runtime jsou zbytečné a lze je oříznout z balené aplikace.</span><span class="sxs-lookup"><span data-stu-id="30ec3-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

> [!NOTE]
> <span data-ttu-id="30ec3-111">Oříznutí je experimentální funkce v rozhraní .NET Core 3.1 a je k dispozici _pouze_ pro aplikace, které jsou publikovány samostatně.</span><span class="sxs-lookup"><span data-stu-id="30ec3-111">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="trim-your-application"></a><span data-ttu-id="30ec3-112">Oříznutí aplikace</span><span class="sxs-lookup"><span data-stu-id="30ec3-112">Trim your application</span></span>

<span data-ttu-id="30ec3-113">Následující příklad ukazuje, jak oříznout aplikaci pomocí příkazu [dotnet publish:](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="30ec3-113">The following example shows how to trim your application using the [dotnet publish](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

<span data-ttu-id="30ec3-114">Funkce oříznutí funguje tak, že zkoumá binární soubory aplikace, aby zjistila a vytvořila graf požadovaných sestav za běhu.</span><span class="sxs-lookup"><span data-stu-id="30ec3-114">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="30ec3-115">Zbývající sestavení za běhu, na která se neodkazuje, jsou oříznuta.</span><span class="sxs-lookup"><span data-stu-id="30ec3-115">The remaining runtime assemblies that aren't referenced are trimmed.</span></span>

## <a name="trimming-issues-when-using-reflection"></a><span data-ttu-id="30ec3-116">Problémy s oříznutím při použití odrazu</span><span class="sxs-lookup"><span data-stu-id="30ec3-116">Trimming issues when using reflection</span></span>

<span data-ttu-id="30ec3-117">Existují scénáře, ve kterých funkce oříznutí se nezdaří rozpoznat odkazy.</span><span class="sxs-lookup"><span data-stu-id="30ec3-117">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="30ec3-118">Například aplikace, která používá reflexe může spustit do tohoto problému, protože závislost na sestavení bude známa pouze v době běhu.</span><span class="sxs-lookup"><span data-stu-id="30ec3-118">For example, an application that uses reflection could run into this issue because the dependency on the assembly will only be known at run time.</span></span>

<span data-ttu-id="30ec3-119">Oříznutí je pouze problém, pokud použití reflexe závisí na sestavení za běhu, který není odkazován přímo.</span><span class="sxs-lookup"><span data-stu-id="30ec3-119">Trimming is only a problem if the reflection usage depends on a runtime assembly that isn't referenced directly.</span></span> <span data-ttu-id="30ec3-120">Mějte na paměti, že kód aplikace nemusí používat reflexe přímo, ale sestavení jiného výrobce, na které odkazujete, jej může používat.</span><span class="sxs-lookup"><span data-stu-id="30ec3-120">Keep in mind that your application code may not be using reflection directly, but a third-party assembly you're referencing may be using it.</span></span>

<span data-ttu-id="30ec3-121">Když kód odkazuje na rozhraní API prostřednictvím reflexe a nechcete, aby propojovací program oříznout sestavení, které obsahuje toto rozhraní API, můžete upravit soubor projektu vyloučit sestavení z procesu oříznutí.</span><span class="sxs-lookup"><span data-stu-id="30ec3-121">When the code is referencing an API through reflection and you don't want the linker to trim the assembly that contains that API, you can modify your project file to exclude the assembly from the trimming process.</span></span> <span data-ttu-id="30ec3-122">Následující příklad ukazuje, jak zabránit `System.Security` oříznutí volaného sestavení:</span><span class="sxs-lookup"><span data-stu-id="30ec3-122">The following example shows how to prevent an assembly called `System.Security` from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="30ec3-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="30ec3-123">See also</span></span>

- [<span data-ttu-id="30ec3-124">Nasazení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="30ec3-124">.NET Core application deployment</span></span>](index.md)
