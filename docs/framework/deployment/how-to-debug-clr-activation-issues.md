---
title: 'Postupy: Ladění problémů aktivace CLR'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89724e9a322f2f28dbe5d18ae697acbdd0a32d8e
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041619"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="cf86c-102">Postupy: Ladění problémů aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="cf86c-102">How to: Debug CLR Activation Issues</span></span>
<span data-ttu-id="cf86c-103">Pokud narazíte na problémy při získávání aplikace na spouštění se správnou verzí modulu common language runtime (CLR), můžete zobrazit a ladit protokoly aktivace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cf86c-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="cf86c-104">Tyto protokoly mohou být velmi užitečné při určování původní příčinu chyby aktivace, když aplikace načte jinou verzi CLR, než se očekávalo nebo nebude vůbec načíst modul CLR.</span><span class="sxs-lookup"><span data-stu-id="cf86c-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="cf86c-105">[Rozhraní .NET Framework – chyby inicializace: Správa uživatelskou zkušenost](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) popisuje prostředí, když pro aplikaci nebyl nalezen žádný CLR.</span><span class="sxs-lookup"><span data-stu-id="cf86c-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>  
  
 <span data-ttu-id="cf86c-106">Protokolování aktivace modulu CLR může být povoleno systémová pomocí klíčem HKEY_LOCAL_MACHINE registru nebo systémové proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="cf86c-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="cf86c-107">Vygeneruje se protokol až do položky registru nebo proměnné prostředí se odebere.</span><span class="sxs-lookup"><span data-stu-id="cf86c-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="cf86c-108">Alternativně můžete uživatele nebo proměnné prostředí místní proces povolit protokolování pomocí různých rozsahu a doby trvání.</span><span class="sxs-lookup"><span data-stu-id="cf86c-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>  
  
 <span data-ttu-id="cf86c-109">Protokoly aktivace CLR neměly by být zaměňovány s [protokoly vazeb sestavení](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), které jsou úplně jiného.</span><span class="sxs-lookup"><span data-stu-id="cf86c-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>  
  
## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="cf86c-110">Povolení protokolování aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="cf86c-110">To enable CLR activation logging</span></span>  
  
#### <a name="using-the-registry"></a><span data-ttu-id="cf86c-111">Pomocí registru</span><span class="sxs-lookup"><span data-stu-id="cf86c-111">Using the registry</span></span>  
  
1.  <span data-ttu-id="cf86c-112">V editoru registru přejděte na HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na 32bitovém počítači) nebo HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework složka (na 64bitovém počítači).</span><span class="sxs-lookup"><span data-stu-id="cf86c-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>  
  
2.  <span data-ttu-id="cf86c-113">Přidejte hodnotu řetězce s názvem `CLRLoadLogDir`a nastavte ho na úplnou cestu existující adresář ve kterém chcete ukládat protokoly aktivace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cf86c-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
 <span data-ttu-id="cf86c-114">Aktivace protokolování zůstane povolena, dokud neodeberete řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cf86c-114">Activation logging remains enabled until you remove the string value.</span></span>  
  
#### <a name="using-an-environment-variable"></a><span data-ttu-id="cf86c-115">Pomocí proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="cf86c-115">Using an environment variable</span></span>  
  
-   <span data-ttu-id="cf86c-116">Nastavte `COMPLUS_CLRLoadLogDir` proměnné prostředí na řetězec, který představuje úplnou cestu existující adresář, kam chcete ukládat protokoly aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="cf86c-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
     <span data-ttu-id="cf86c-117">Určuje svého oboru, jak nastavit proměnnou prostředí:</span><span class="sxs-lookup"><span data-stu-id="cf86c-117">How you set the environment variable determines its scope:</span></span>  
  
    -   <span data-ttu-id="cf86c-118">Pokud ji nastavíte na úrovni systému, aktivace je povoleno protokolování pro všechny aplikace rozhraní .NET Framework na tomto počítači až do odebrání proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="cf86c-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="cf86c-119">Pokud ji nastavíte na úrovni uživatele, aktivaci protokolování je povoleno pouze pro aktuální uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="cf86c-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="cf86c-120">Protokolování pokračuje, dokud je proměnná prostředí se odebere.</span><span class="sxs-lookup"><span data-stu-id="cf86c-120">Logging continues until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="cf86c-121">Pokud ji nastavíte z v rámci procesu před načtením modulu CLR, je povoleno protokolování aktivace až do doby ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="cf86c-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>  
  
    -   <span data-ttu-id="cf86c-122">Pokud ji nastavíte na příkazovém řádku před spuštěním aplikace, je povoleno protokolování aktivace pro každou aplikaci, která se spouští z tohoto příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cf86c-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>  
  
     <span data-ttu-id="cf86c-123">Například pro ukládání protokolů aktivace v adresáři c:\clrloadlogs s rozsahem úrovni procesu, otevřete okno příkazového řádku a zadejte následující příkaz před spuštěním aplikace:</span><span class="sxs-lookup"><span data-stu-id="cf86c-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a><span data-ttu-id="cf86c-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf86c-124">Example</span></span>  
 <span data-ttu-id="cf86c-125">Protokoly aktivace CLR poskytují velké množství dat o CLR – aktivace a použití modulu CLR rozhraní API pro hostování.</span><span class="sxs-lookup"><span data-stu-id="cf86c-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="cf86c-126">Většina těchto dat se používá interně společností Microsoft, ale některá data může být také užitečný pro vývojáře, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="cf86c-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>  
  
 <span data-ttu-id="cf86c-127">Protokol rozhraní API pro hostování CLR odpovídá pořadí, ve kterém byly volány.</span><span class="sxs-lookup"><span data-stu-id="cf86c-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="cf86c-128">Zahrnuje také užitečné údaje o sadu instalovaných modulů runtime v počítači nalezen.</span><span class="sxs-lookup"><span data-stu-id="cf86c-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="cf86c-129">Formát protokolu aktivace CLR není samotné popsané, ale je možné podpory vývojářům, kteří potřebují k vyřešení problémů aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="cf86c-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf86c-130">Aktivace protokolu nelze otevřít, dokud proces, který používá modul CLR byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="cf86c-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf86c-131">Protokoly aktivace CLR nejsou lokalizovány; generují se vždy v anglickém jazyce.</span><span class="sxs-lookup"><span data-stu-id="cf86c-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>  
  
 <span data-ttu-id="cf86c-132">V následujícím příkladu protokolu aktivace je velmi užitečné informace zvýrazní a popsané po protokolu.</span><span class="sxs-lookup"><span data-stu-id="cf86c-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>  
  
```  
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
  
-   <span data-ttu-id="cf86c-133">**Načítání protokolu modulu CLR** poskytuje cestu ke spustitelnému souboru, který spustil proces, který zavedl spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cf86c-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="cf86c-134">Všimněte si, že to může být nativních hostitelů.</span><span class="sxs-lookup"><span data-stu-id="cf86c-134">Note that this could be a native host.</span></span>  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   <span data-ttu-id="cf86c-135">**Nainstalovat modul Runtime** je sada CLR verze nainstalované na počítači, které jsou kandidáty pro žádost o aktivaci.</span><span class="sxs-lookup"><span data-stu-id="cf86c-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   <span data-ttu-id="cf86c-136">**sestaveno s verzí** verzi CLR, který byl použit k vytvoření binární soubor, který byl poskytnut do metody, jako je [iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="cf86c-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   <span data-ttu-id="cf86c-137">**instalace funkcí na vyžádání** odkazuje na povolení rozhraní .NET Framework 3.5 v systému Windows 8.</span><span class="sxs-lookup"><span data-stu-id="cf86c-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="cf86c-138">Zobrazit [rozhraní .NET Framework – chyby inicializace: Správa zkušeností uživatele](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Další informace o tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="cf86c-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cf86c-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf86c-139">See Also</span></span>  
- [<span data-ttu-id="cf86c-140">Nasazení</span><span class="sxs-lookup"><span data-stu-id="cf86c-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)  
- [<span data-ttu-id="cf86c-141">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5</span><span class="sxs-lookup"><span data-stu-id="cf86c-141">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
