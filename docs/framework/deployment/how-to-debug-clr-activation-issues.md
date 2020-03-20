---
title: Jak ladit problémy s aktivací CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 602ee3c88237a902d48339836fbe25f636ae9705
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716511"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="7aab3-102">Jak ladit problémy s aktivací CLR</span><span class="sxs-lookup"><span data-stu-id="7aab3-102">How to debug CLR activation issues</span></span>

<span data-ttu-id="7aab3-103">Pokud narazíte na problémy při získávání aplikace ke spuštění se správnou verzí clr jazyka, můžete zobrazit a ladit protokoly aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="7aab3-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="7aab3-104">Tyto protokoly mohou být velmi užitečné při určování hlavní příčinu problému aktivace, když aplikace buď načte jinou verzi CLR, než bylo očekáváno, nebo nenačte CLR vůbec.</span><span class="sxs-lookup"><span data-stu-id="7aab3-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="7aab3-105">[Chyby inicializace rozhraní .NET Framework: Správa uživatelského prostředí](initialization-errors-managing-the-user-experience.md) popisuje prostředí, kdy pro aplikaci není nalezen žádný clr.</span><span class="sxs-lookup"><span data-stu-id="7aab3-105">The [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="7aab3-106">Protokolování aktivace CLR lze povolit v celém systému pomocí klíče registru HKEY_LOCAL_MACHINE nebo proměnné systémového prostředí.</span><span class="sxs-lookup"><span data-stu-id="7aab3-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="7aab3-107">Protokol bude generován, dokud nebude odebrána položka registru nebo proměnná prostředí.</span><span class="sxs-lookup"><span data-stu-id="7aab3-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="7aab3-108">Alternativně můžete použít proměnnou prostředí uživatele nebo místního procesu k povolení protokolování s jiným rozsahem a dobou trvání.</span><span class="sxs-lookup"><span data-stu-id="7aab3-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="7aab3-109">Protokoly aktivace CLR by neměly být zaměňovány s [protokoly vazby sestavení](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou zcela odlišné.</span><span class="sxs-lookup"><span data-stu-id="7aab3-109">CLR activation logs shouldn't be confused with [assembly binding logs](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="7aab3-110">Povolení protokolování aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="7aab3-110">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="7aab3-111">Použití registru</span><span class="sxs-lookup"><span data-stu-id="7aab3-111">Using the registry</span></span>

1. <span data-ttu-id="7aab3-112">V Editoru registru přejděte na\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework (v 32bitovém počítači) nebo HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework (v 64bitovém počítači).</span><span class="sxs-lookup"><span data-stu-id="7aab3-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="7aab3-113">Přidejte hodnotu `CLRLoadLogDir`řetězce s názvem a nastavte ji na úplnou cestu existujícího adresáře, do kterého chcete uložit protokoly aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="7aab3-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="7aab3-114">Protokolování aktivace zůstane povoleno, dokud neodeberete hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="7aab3-114">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="7aab3-115">Použití proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="7aab3-115">Using an environment variable</span></span>

- <span data-ttu-id="7aab3-116">Nastavte `COMPLUS_CLRLoadLogDir` proměnnou prostředí na řetězec, který představuje úplnou cestu existujícího adresáře, do kterého chcete uložit protokoly aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="7aab3-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="7aab3-117">Způsob nastavení proměnné prostředí určuje její obor:</span><span class="sxs-lookup"><span data-stu-id="7aab3-117">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="7aab3-118">Pokud ji nastavíte na úrovni systému, protokolování aktivace je povoleno pro všechny aplikace rozhraní .NET Framework v tomto počítači, dokud nebude proměnná prostředí odebrána.</span><span class="sxs-lookup"><span data-stu-id="7aab3-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="7aab3-119">Pokud ji nastavíte na úrovni uživatele, protokolování aktivace je povoleno pouze pro aktuální uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="7aab3-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="7aab3-120">Protokolování pokračuje, dokud není odebrána proměnná prostředí.</span><span class="sxs-lookup"><span data-stu-id="7aab3-120">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="7aab3-121">Pokud jej nastavíte z procesu před načtením CLR, protokolování aktivace je povolena, dokud proces neskončí.</span><span class="sxs-lookup"><span data-stu-id="7aab3-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="7aab3-122">Pokud ji nastavíte na příkazovém řádku před spuštěním aplikace, protokolování aktivace je povoleno pro všechny aplikace, které jsou spuštěny z tohoto příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7aab3-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="7aab3-123">Chcete-li například uložit protokoly aktivace do adresáře c:\clloadlogs s rozsahem na úrovni procesu, otevřete před spuštěním aplikace následující okno a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7aab3-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="7aab3-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="7aab3-124">Example</span></span>

<span data-ttu-id="7aab3-125">Protokoly aktivace CLR poskytují velké množství dat o aktivaci CLR a použití hostitelských api CLR.</span><span class="sxs-lookup"><span data-stu-id="7aab3-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="7aab3-126">Většina těchto dat je používána interně společností Microsoft, ale některá data mohou být také užitečná pro vývojáře, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="7aab3-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="7aab3-127">Protokol odráží pořadí, ve kterém byly volány CLR hostování API.</span><span class="sxs-lookup"><span data-stu-id="7aab3-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="7aab3-128">Obsahuje také užitečná data o sadě nainstalovaných runtimes zjištěných v počítači.</span><span class="sxs-lookup"><span data-stu-id="7aab3-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="7aab3-129">Formát protokolu aktivace CLR není sám zdokumentován, ale může být použit k pomoci vývojářům, kteří potřebují vyřešit problémy s aktivací CLR.</span><span class="sxs-lookup"><span data-stu-id="7aab3-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="7aab3-130">Protokol aktivace nelze otevřít, dokud nebude ukončen proces, který používá clr.</span><span class="sxs-lookup"><span data-stu-id="7aab3-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="7aab3-131">Protokoly aktivace CLR nejsou lokalizovány. jsou vždy generovány v anglickém jazyce.</span><span class="sxs-lookup"><span data-stu-id="7aab3-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="7aab3-132">V následujícím příkladu protokolu aktivace jsou zvýrazněny a popsány nejužitečnější informace za protokolem.</span><span class="sxs-lookup"><span data-stu-id="7aab3-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

```output
532,205950.367,CLR Loading log for C:\Tests\myapp.exe
532,205950.367,Log started at 4:26:12 PM on 10/6/2011
532,205950.367,-----------------------------------
532,205950.382,FunctionCall: _CorExeMain
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
532,205950.382,Input values for ComputeVersionString follow this line
532,205950.382,-----------------------------------
532,205950.382,Default Application Name: C:\Tests\myapp.exe
532,205950.382,IsLegacyBind is: 0
532,205950.382,IsCapped is 0
532,205950.382,SkuCheckFlags are 0
532,205950.382,ShouldEmulateExeLaunch is 0
532,205950.382,LegacyBindRequired is 0
532,205950.382,-----------------------------------
532,205950.382,Parsing config file: C:\Tests\myapp.exe
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.
532,205950.398,SEM_FAILCRITICALERRORS is set to 0
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
532,205950.398,FunctionCall: RealDllMain. Reason: 0
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0
```

- <span data-ttu-id="7aab3-133">**Protokol načítání CLR** poskytuje cestu ke spustitelnému souboru, který spustil proces, který načetl spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7aab3-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="7aab3-134">Všimněte si, že to může být nativní hostitel.</span><span class="sxs-lookup"><span data-stu-id="7aab3-134">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="7aab3-135">**Nainstalovaný runtime** je sada verzí CLR nainstalovaných v počítači, které jsou kandidáty pro požadavek na aktivaci.</span><span class="sxs-lookup"><span data-stu-id="7aab3-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="7aab3-136">**postavens verzí** je verze CLR, která byla použita k sestavení binárního souboru, který byl poskytnut metodě, jako je [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="7aab3-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="7aab3-137">**instalace funkce na vyžádání** odkazuje na povolení rozhraní .NET Framework 3.5 v systému Windows 8.</span><span class="sxs-lookup"><span data-stu-id="7aab3-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="7aab3-138">Další informace o tomto scénáři naleznete v [tématu Chyby inicializace rozhraní .NET Framework: Správa uživatelského prostředí.](initialization-errors-managing-the-user-experience.md)</span><span class="sxs-lookup"><span data-stu-id="7aab3-138">See [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="7aab3-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aab3-139">See also</span></span>

- [<span data-ttu-id="7aab3-140">Nasazení</span><span class="sxs-lookup"><span data-stu-id="7aab3-140">Deployment</span></span>](index.md)
- [<span data-ttu-id="7aab3-141">Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="7aab3-141">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
