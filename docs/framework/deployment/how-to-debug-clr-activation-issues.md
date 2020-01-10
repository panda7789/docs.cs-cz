---
title: Jak ladit problémy s aktivací CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 602ee3c88237a902d48339836fbe25f636ae9705
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716511"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="bc8aa-102">Jak ladit problémy s aktivací CLR</span><span class="sxs-lookup"><span data-stu-id="bc8aa-102">How to debug CLR activation issues</span></span>

<span data-ttu-id="bc8aa-103">Pokud narazíte na problémy při provádění aplikace se správnou verzí modulu CLR (Common Language Runtime), můžete zobrazit a ladit aktivační protokoly CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="bc8aa-104">Tyto protokoly můžou být velmi užitečné při určování hlavní příčiny problému s aktivací, když vaše aplikace buď načte jinou verzi CLR, než se očekávalo, nebo vůbec nenačte CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="bc8aa-105">[Chyby inicializace .NET Framework: Správa uživatelského prostředí](initialization-errors-managing-the-user-experience.md) , které popisuje prostředí, když pro aplikaci není nalezeno CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-105">The [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="bc8aa-106">Protokolování aktivace CLR lze povolit v rámci systému pomocí HKEY_LOCAL_MACHINE klíče registru nebo proměnné prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="bc8aa-107">Protokol bude vygenerován, dokud nebude odebrána položka registru nebo proměnná prostředí.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="bc8aa-108">Alternativně můžete použít proměnnou uživatelského prostředí nebo uživatele nebo procesu k povolení protokolování s jiným rozsahem a dobou trvání.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="bc8aa-109">Protokoly aktivace CLR by se neměly zaměňovat s [protokoly vazeb sestavení](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou zcela odlišné.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-109">CLR activation logs shouldn't be confused with [assembly binding logs](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="bc8aa-110">Povolení protokolování aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="bc8aa-110">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="bc8aa-111">Použití registru</span><span class="sxs-lookup"><span data-stu-id="bc8aa-111">Using the registry</span></span>

1. <span data-ttu-id="bc8aa-112">V editoru registru přejděte na HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\\. NETFramework (na 32 počítači) nebo\\HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft. NETFramework složka (na 64 počítači).</span><span class="sxs-lookup"><span data-stu-id="bc8aa-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="bc8aa-113">Přidejte řetězcovou hodnotu s názvem `CLRLoadLogDir`a nastavte ji na úplnou cestu k existujícímu adresáři, kam chcete ukládat protokoly aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="bc8aa-114">Protokolování aktivace zůstane povolené, dokud neodeberete řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-114">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="bc8aa-115">Použití proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="bc8aa-115">Using an environment variable</span></span>

- <span data-ttu-id="bc8aa-116">Nastavte proměnnou prostředí `COMPLUS_CLRLoadLogDir` na řetězec, který představuje úplnou cestu k existujícímu adresáři, do kterého chcete ukládat protokoly aktivace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="bc8aa-117">Způsob nastavení proměnné prostředí určuje jeho rozsah:</span><span class="sxs-lookup"><span data-stu-id="bc8aa-117">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="bc8aa-118">Pokud nastavíte tuto možnost na úrovni systému, povolí se protokolování aktivace pro všechny .NET Framework aplikace na daném počítači, dokud se neodebere proměnná prostředí.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="bc8aa-119">Pokud nastavíte tuto možnost na úrovni uživatele, protokolování aktivace je povoleno pouze pro aktuální uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="bc8aa-120">Protokolování pokračuje, dokud nebude proměnná prostředí odebrána.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-120">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="bc8aa-121">Pokud jej před načtením modulu CLR nastavíte v rámci procesu, protokolování aktivace bude povoleno až do ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="bc8aa-122">Pokud ho před spuštěním aplikace nastavíte na příkazovém řádku, povolí se protokolování aktivace pro všechny aplikace, které se spouštějí z tohoto příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="bc8aa-123">Chcete-li například uložit aktivační protokoly v adresáři c:\clrloadlogs s rozsahem na úrovni procesu, otevřete okno příkazového řádku a před spuštěním aplikace zadejte následující text:</span><span class="sxs-lookup"><span data-stu-id="bc8aa-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="bc8aa-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc8aa-124">Example</span></span>

<span data-ttu-id="bc8aa-125">Protokoly aktivace CLR poskytují velké množství dat o aktivaci CLR a použití rozhraní API pro hostování rozhraní CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="bc8aa-126">Většinu těchto dat používá společnost Microsoft interně, ale některá z nich mohou být užitečná také pro vývojáře, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="bc8aa-127">Protokol odráží pořadí, ve kterém byly volány rozhraní API hostování modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="bc8aa-128">Zahrnuje také užitečná data o sadě nainstalovaných modulů runtime zjištěných v počítači.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="bc8aa-129">Formát protokolu aktivace CLR není dokumentován, ale lze jej použít k podpoře vývojářů, kteří potřebují vyřešit problémy s aktivací CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="bc8aa-130">Aktivační protokol nelze otevřít, dokud nebude ukončen proces, který používá modul CLR.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="bc8aa-131">Protokoly aktivace CLR nejsou lokalizovány; jsou vždycky vygenerované v anglickém jazyce.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="bc8aa-132">V následujícím příkladu aktivačního protokolu jsou nejužitečnější informace zvýrazněny a popsány po protokolu.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

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

- <span data-ttu-id="bc8aa-133">**Protokol načítání CLR** poskytuje cestu ke spustitelnému souboru, který spustil proces, který zavedl spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="bc8aa-134">Všimněte si, že se může jednat o nativního hostitele.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-134">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="bc8aa-135">**Instalovaný modul runtime** je sada verzí CLR nainstalovaná na počítači, které jsou kandidáty na žádost o aktivaci.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="bc8aa-136">**sestaveno s verzí** je verze modulu CLR, která byla použita k sestavení binárního souboru, který byl poskytnut metodě jako [ICLRMetaHostPolicy –:: GetRequestedRuntime –](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="bc8aa-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="bc8aa-137">**instalace funkcí na vyžádání** odkazuje na povolení .NET Framework 3,5 ve Windows 8.</span><span class="sxs-lookup"><span data-stu-id="bc8aa-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="bc8aa-138">Další informace o tomto scénáři najdete v tématu [.NET Framework chyby inicializace: Správa uživatelského prostředí](initialization-errors-managing-the-user-experience.md) .</span><span class="sxs-lookup"><span data-stu-id="bc8aa-138">See [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="bc8aa-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc8aa-139">See also</span></span>

- [<span data-ttu-id="bc8aa-140">Nasazení</span><span class="sxs-lookup"><span data-stu-id="bc8aa-140">Deployment</span></span>](index.md)
- [<span data-ttu-id="bc8aa-141">Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="bc8aa-141">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
