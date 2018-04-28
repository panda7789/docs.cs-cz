---
title: Nasazení aplikace .NET core
description: Nasazení aplikace .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 5b8d49fd70b6e6b136a00aa0f7d7070bdd5a401a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-application-deployment"></a><span data-ttu-id="3a360-103">Nasazení aplikace .NET core</span><span class="sxs-lookup"><span data-stu-id="3a360-103">.NET Core application deployment</span></span>

<span data-ttu-id="3a360-104">Můžete vytvořit dva typy nasazení pro aplikace .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3a360-104">You can create two types of deployments for .NET Core applications:</span></span>

- <span data-ttu-id="3a360-105">Nasazení Framework závislé.</span><span class="sxs-lookup"><span data-stu-id="3a360-105">Framework-dependent deployment.</span></span> <span data-ttu-id="3a360-106">Jak již název napovídá, nasazení závislé na framework (disketové jednotky) spoléhá na přítomnost sdílené systémové verze .NET Core v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="3a360-106">As the name implies, framework-dependent deployment (FDD) relies on the presence of a shared system-wide version of .NET Core on the target system.</span></span> <span data-ttu-id="3a360-107">Protože .NET Core již existuje, vaše aplikace je také přenosné mezi instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a360-107">Because .NET Core is already present, your app is also portable between installations of .NET Core.</span></span> <span data-ttu-id="3a360-108">Vaše aplikace obsahuje pouze vlastní kód a všechny závislosti třetích stran, které jsou mimo na knihovny .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a360-108">Your app contains only its own code and any third-party dependencies that are outside of the .NET Core libraries.</span></span> <span data-ttu-id="3a360-109">Obsahovat FDDs *.dll* soubory, které může být spuštěn s použitím [dotnet nástroj](../tools/dotnet.md) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3a360-109">FDDs contain *.dll* files that can be launched by using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span> <span data-ttu-id="3a360-110">Například `dotnet app.dll` běží aplikace s názvem `app`.</span><span class="sxs-lookup"><span data-stu-id="3a360-110">For example, `dotnet app.dll` runs an application named `app`.</span></span>

- <span data-ttu-id="3a360-111">Samostatná nasazení.</span><span class="sxs-lookup"><span data-stu-id="3a360-111">Self-contained deployment.</span></span> <span data-ttu-id="3a360-112">Na rozdíl od disketové jednotky není úplný a samostatný nasazení (SCD) závisí na přítomnost sdílené komponenty v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="3a360-112">Unlike FDD, a self-contained deployment (SCD) doesn't rely on the presence of shared components on the target system.</span></span> <span data-ttu-id="3a360-113">Všechny součásti, včetně knihovny .NET Core a na .NET Core runtime, jsou součástí aplikace a jsou izolované od ostatních aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a360-113">All components, including both the .NET Core libraries and the .NET Core runtime, are included with the application and are isolated from other .NET Core applications.</span></span> <span data-ttu-id="3a360-114">SCDs zahrnují spustitelný soubor (například *app.exe* na platformách systému Windows pro aplikaci s názvem `app`), což je přejmenován verzi specifické pro platformu .NET Core hostitele a *.dll* souboru (například *app.dll*), což je skutečný aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a360-114">SCDs include an executable (such as *app.exe* on Windows platforms for an application named `app`), which is  a renamed version of the platform-specific .NET Core host, and a *.dll* file (such as *app.dll*), which is the actual application.</span></span>

## <a name="framework-dependent-deployments-fdd"></a><span data-ttu-id="3a360-115">Nasazení závislé na Framework (disketové jednotky)</span><span class="sxs-lookup"><span data-stu-id="3a360-115">Framework-dependent deployments (FDD)</span></span>

<span data-ttu-id="3a360-116">Pro disketové jednotky nasaďte jenom aplikace a všechny závislosti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="3a360-116">For an FDD, you deploy only your app and any third-party dependencies.</span></span> <span data-ttu-id="3a360-117">Nemusíte nasazovat .NET Core, vzhledem k tomu, že aplikace bude používat verzi .NET Core, který se nachází v cílovém systému.</span><span class="sxs-lookup"><span data-stu-id="3a360-117">You don't have to deploy .NET Core, since your app will use the version of .NET Core that's present on the target system.</span></span> <span data-ttu-id="3a360-118">Toto je výchozí model nasazení pro aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a360-118">This is the default deployment model for .NET Core apps.</span></span>

### <a name="why-create-a-framework-dependent-deployment"></a><span data-ttu-id="3a360-119">Proč vytvoření nasazení závislé na framework?</span><span class="sxs-lookup"><span data-stu-id="3a360-119">Why create a framework-dependent deployment?</span></span>

<span data-ttu-id="3a360-120">Nasazení disketové jednotky má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="3a360-120">Deploying an FDD has a number of advantages:</span></span>

- <span data-ttu-id="3a360-121">Nemusíte definovat cílový operační systémy, které vaše aplikace .NET Core poběží na předem.</span><span class="sxs-lookup"><span data-stu-id="3a360-121">You don't have to define the target operating systems that your .NET Core app will run on in advance.</span></span> <span data-ttu-id="3a360-122">Protože .NET Core používá běžný formát souboru PE pro spustitelné soubory a knihovny bez ohledu na operační systém, můžete provést .NET Core aplikace bez ohledu na příslušný operační systém.</span><span class="sxs-lookup"><span data-stu-id="3a360-122">Because .NET Core uses a common PE file format for executables and libraries regardless of operating system, .NET Core can execute your app regardless of the underlying operating system.</span></span> <span data-ttu-id="3a360-123">Další informace o formátu souboru PE najdete v tématu [formát souboru sestavení .NET](../../standard/assembly-format.md).</span><span class="sxs-lookup"><span data-stu-id="3a360-123">For more information on the PE file format, see [.NET Assembly File Format](../../standard/assembly-format.md).</span></span>

- <span data-ttu-id="3a360-124">Velikost vašeho nasazení balíčku je malá.</span><span class="sxs-lookup"><span data-stu-id="3a360-124">The size of your deployment package is small.</span></span> <span data-ttu-id="3a360-125">Pouze nasazení aplikace a jeho závislé součásti, není .NET Core sám sebe.</span><span class="sxs-lookup"><span data-stu-id="3a360-125">You only deploy your app and its dependencies, not .NET Core itself.</span></span>

- <span data-ttu-id="3a360-126">Více aplikací použít stejné instalace .NET Core, což snižuje obou disku místa a použití paměti v hostitelských systémech.</span><span class="sxs-lookup"><span data-stu-id="3a360-126">Multiple apps use the same .NET Core installation, which reduces both disk space and memory usage on host systems.</span></span>

<span data-ttu-id="3a360-127">Existují také několik nevýhody:</span><span class="sxs-lookup"><span data-stu-id="3a360-127">There are also a few disadvantages:</span></span>

- <span data-ttu-id="3a360-128">Aplikace lze spustit pouze v případě, že verze .NET Core, která cílí nebo novější, je již nainstalována v hostitelském systému.</span><span class="sxs-lookup"><span data-stu-id="3a360-128">Your app can run only if the version of .NET Core that you target, or a later version, is already installed on the host system.</span></span>

- <span data-ttu-id="3a360-129">Je možné pro .NET Core runtime a knihovny, chcete-li změnit bez vašeho vědomí v budoucích vezích se.</span><span class="sxs-lookup"><span data-stu-id="3a360-129">It's possible for the .NET Core runtime and libraries to change without your knowledge in future releases.</span></span> <span data-ttu-id="3a360-130">Ve výjimečných případech může změnit chování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a360-130">In rare cases, this may change the behavior of your app.</span></span>

## <a name="self-contained-deployments-scd"></a><span data-ttu-id="3a360-131">Samostatná nasazení (SCD)</span><span class="sxs-lookup"><span data-stu-id="3a360-131">Self-contained deployments (SCD)</span></span>

<span data-ttu-id="3a360-132">Samostatná nasazení Nasaďte aplikaci a všechny požadované závislosti společně s verzi .NET Core, který jste použili k vytvoření aplikace třetích stran.</span><span class="sxs-lookup"><span data-stu-id="3a360-132">For a self-contained deployment, you deploy your app and any required third-party dependencies along with the version of .NET Core that you used to build the app.</span></span> <span data-ttu-id="3a360-133">Vytvoření SCD neobsahuje [nativní závislosti .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na různých platformách, takže tyto musí být před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a360-133">Creating an SCD doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) on various platforms, so these must be present before the app runs.</span></span>

<span data-ttu-id="3a360-134">Nasazení disketové jednotky a SCD použít samostatné hostitele spustitelné soubory, můžete si hostitel spustitelný soubor SCD s podpisem vydavatele.</span><span class="sxs-lookup"><span data-stu-id="3a360-134">FDD and SCD deployments use separate host executables, so you can sign a host executable for an SCD with your publisher signature.</span></span>

### <a name="why-deploy-a-self-contained-deployment"></a><span data-ttu-id="3a360-135">Proč samostatná nasazení?</span><span class="sxs-lookup"><span data-stu-id="3a360-135">Why deploy a self-contained deployment?</span></span>

<span data-ttu-id="3a360-136">Nasazení samostatná nasazení má dvě hlavní výhody:</span><span class="sxs-lookup"><span data-stu-id="3a360-136">Deploying a Self-contained deployment has two major advantages:</span></span>

- <span data-ttu-id="3a360-137">Máte jedinou ovládacího prvku na verzi .NET Core, který je nasazen s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="3a360-137">You have sole control of the version of .NET Core that is deployed with your app.</span></span> <span data-ttu-id="3a360-138">.NET core můžete obsloužení pouze můžete.</span><span class="sxs-lookup"><span data-stu-id="3a360-138">.NET Core can be serviced only by you.</span></span>

- <span data-ttu-id="3a360-139">Můžete si být jistí, že cílový systém můžete spustit aplikace .NET Core vzhledem k tomu, že zadáváte verzi .NET Core, který bude spuštěn na.</span><span class="sxs-lookup"><span data-stu-id="3a360-139">You can be assured that the target system can run your .NET Core app, since you're providing the version of .NET Core that it will run on.</span></span>

<span data-ttu-id="3a360-140">Má také počet nevýhody:</span><span class="sxs-lookup"><span data-stu-id="3a360-140">It also has a number of disadvantages:</span></span>

- <span data-ttu-id="3a360-141">Protože .NET Core je zahrnutý v balíčku pro nasazení, je nutné vybrat cílových platforem, pro které je předem vytvořit balíčky pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="3a360-141">Because .NET Core is included in your deployment package, you must select the target platforms for which you build deployment packages in advance.</span></span>

- <span data-ttu-id="3a360-142">Velikost vašeho nasazení balíčku je relativně velké vzhledem k tomu, že je nutné zahrnout .NET Core a také vaše aplikace a jeho závislosti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="3a360-142">The size of your deployment package is relatively large, since you have to include .NET Core as well as your app and its third-party dependencies.</span></span>

- <span data-ttu-id="3a360-143">Nasazování mnoha nezávislý aplikací .NET Core k systému můžou zabrat poměrně velké množství místa na disku, od každého duplikáty aplikace .NET Core soubory.</span><span class="sxs-lookup"><span data-stu-id="3a360-143">Deploying numerous self-contained .NET Core apps to a system can consume significant amounts of disk space, since each app duplicates .NET Core files.</span></span>

## <a name="step-by-step-examples"></a><span data-ttu-id="3a360-144">Podrobné příklady</span><span class="sxs-lookup"><span data-stu-id="3a360-144">Step-by-step examples</span></span>

<span data-ttu-id="3a360-145">Podrobné příklady nasazení aplikací .NET Core pomocí nástrojů příkazového řádku najdete v tématu [nasazení aplikací pro rozhraní .NET Core pomocí nástrojů příkazového řádku](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="3a360-145">For step-by-step examples of deploying .NET Core apps with CLI tools, see [Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md).</span></span> <span data-ttu-id="3a360-146">Podrobné příklady nasazení aplikace .NET Core pomocí sady Visual Studio najdete v tématu [nasazení aplikace .NET Core pomocí sady Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="3a360-146">For step-by-step examples of deploying .NET Core apps with Visual Studio, see [Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md).</span></span> <span data-ttu-id="3a360-147">Každý téma obsahuje příklady následující nasazení:</span><span class="sxs-lookup"><span data-stu-id="3a360-147">Each topic includes examples of the following deployments:</span></span>

- <span data-ttu-id="3a360-148">Nasazení závislé na Framework</span><span class="sxs-lookup"><span data-stu-id="3a360-148">Framework-dependent deployment</span></span>
- <span data-ttu-id="3a360-149">Nasazení závislé na Framework se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="3a360-149">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="3a360-150">Samostatná nasazení</span><span class="sxs-lookup"><span data-stu-id="3a360-150">Self-contained deployment</span></span>
- <span data-ttu-id="3a360-151">Samostatná nasazení se závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="3a360-151">Self-contained deployment with third-party dependencies</span></span>

# <a name="see-also"></a><span data-ttu-id="3a360-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a360-152">See also</span></span>

<span data-ttu-id="3a360-153">[Nasazení aplikací .NET Core pomocí nástrojů příkazového řádku](deploy-with-cli.md) </span><span class="sxs-lookup"><span data-stu-id="3a360-153">[Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md) </span></span>  
<span data-ttu-id="3a360-154">[Nasazení aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md) </span><span class="sxs-lookup"><span data-stu-id="3a360-154">[Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md) </span></span>  
<span data-ttu-id="3a360-155">[Balíčky, Metapackages a architektury](../packages.md) </span><span class="sxs-lookup"><span data-stu-id="3a360-155">[Packages, Metapackages and Frameworks](../packages.md) </span></span>  
[<span data-ttu-id="3a360-156">Katalog .NET core Runtime identifikátor (RID)</span><span class="sxs-lookup"><span data-stu-id="3a360-156">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
