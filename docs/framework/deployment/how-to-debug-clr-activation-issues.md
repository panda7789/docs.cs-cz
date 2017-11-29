---
title: "Postupy: Ladění problémů aktivace CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d923f97b6c3954f07467f9fbfe40913f427bb99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="7a087-102">Postupy: Ladění problémů aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="7a087-102">How to: Debug CLR Activation Issues</span></span>
<span data-ttu-id="7a087-103">Pokud narazíte na potíže při získávání aplikace na spouštění se správnou verzí common language runtime (CLR), můžete zobrazit a ladění protokoly aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="7a087-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="7a087-104">Tyto protokoly může být velmi užitečná při určení příčiny problému aktivace, když aplikace načte různé verze CLR, než se očekávalo nebo vůbec nenačte modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7a087-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="7a087-105">[Rozhraní .NET Framework – chyby inicializace: Správa uživatelské prostředí](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) popisuje možnosti, když se najde žádné CLR pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7a087-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>  
  
 <span data-ttu-id="7a087-106">Protokolování aktivace CLR může být povoleno systémové pomocí klíče registru HKEY_LOCAL_MACHINE nebo systémové proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="7a087-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="7a087-107">V protokolu se budou generovat dokud položku registru nebo proměnná prostředí je odebrat.</span><span class="sxs-lookup"><span data-stu-id="7a087-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="7a087-108">Alternativně můžete použít na uživatele nebo proměnná prostředí místní proces povolení protokolování s jiný rozsah a doba trvání.</span><span class="sxs-lookup"><span data-stu-id="7a087-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>  
  
 <span data-ttu-id="7a087-109">Protokoly aktivace CLR Nezaměňovat s [sestavení – vazby protokolů](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), který se zcela liší.</span><span class="sxs-lookup"><span data-stu-id="7a087-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>  
  
## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="7a087-110">Chcete-li povolit protokolování aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="7a087-110">To enable CLR activation logging</span></span>  
  
#### <a name="using-the-registry"></a><span data-ttu-id="7a087-111">Pomocí klíče registru</span><span class="sxs-lookup"><span data-stu-id="7a087-111">Using the registry</span></span>  
  
1.  <span data-ttu-id="7a087-112">V editoru registru přejděte na HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (v počítači 32bitová verze) nebo HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Složka NETFramework (na 64bitovém počítači).</span><span class="sxs-lookup"><span data-stu-id="7a087-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>  
  
2.  <span data-ttu-id="7a087-113">Přidejte řetězcovou hodnotu s názvem `CLRLoadLogDir`a nastavte ji na úplnou cestu existující adresář kam chcete ukládat aktivační události CLR.</span><span class="sxs-lookup"><span data-stu-id="7a087-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
 <span data-ttu-id="7a087-114">Aktivace protokolování byla povolena, dokud neodeberete hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="7a087-114">Activation logging remains enabled until you remove the string value.</span></span>  
  
#### <a name="using-an-environment-variable"></a><span data-ttu-id="7a087-115">Pomocí proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="7a087-115">Using an environment variable</span></span>  
  
-   <span data-ttu-id="7a087-116">Nastavte `COMPLUS_CLRLoadLogDir` proměnnou prostředí na řetězec, který představuje úplnou cestu existující adresář, kam chcete ukládat aktivační události CLR.</span><span class="sxs-lookup"><span data-stu-id="7a087-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
     <span data-ttu-id="7a087-117">Určuje, jak nastavit proměnnou prostředí svém oboru:</span><span class="sxs-lookup"><span data-stu-id="7a087-117">How you set the environment variable determines its scope:</span></span>  
  
    -   <span data-ttu-id="7a087-118">Pokud je nastavena na úrovni systému, aktivace protokolování je povoleno pro všechny aplikace rozhraní .NET Framework na tomto počítači, dokud se neodstraní proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="7a087-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="7a087-119">Pokud je nastavena na úrovni uživatele, aktivaci protokolování je povolená jenom pro aktuální uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="7a087-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="7a087-120">Protokolování bude pokračovat, dokud se neodstraní proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="7a087-120">Logging continues until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="7a087-121">Pokud jste nastavili z v rámci procesu před načtením modulu CLR, je povoleno protokolování aktivace, dokud se proces ukončí.</span><span class="sxs-lookup"><span data-stu-id="7a087-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>  
  
    -   <span data-ttu-id="7a087-122">Pokud je nastavena na příkazovém řádku před spuštěním aplikace, je povoleno protokolování aktivace pro každou aplikaci, která se spouští z tohoto příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7a087-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>  
  
     <span data-ttu-id="7a087-123">Například k ukládání protokolů aktivace v adresáři c:\clrloadlogs proces úrovni oboru, otevřete okno příkazového řádku a zadejte následující příkaz před spuštěním aplikace:</span><span class="sxs-lookup"><span data-stu-id="7a087-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a><span data-ttu-id="7a087-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a087-124">Example</span></span>  
 <span data-ttu-id="7a087-125">Protokoly aktivace CLR poskytují velké množství dat o CLR – aktivace a použití modulu CLR hostování rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7a087-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="7a087-126">Většina těchto dat se používá interně společností Microsoft, ale některá data může být také užitečné pro vývojáře, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="7a087-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>  
  
 <span data-ttu-id="7a087-127">Protokol odráží pořadí, v jakém modul CLR, který je hostitelem rozhraní API byla volána.</span><span class="sxs-lookup"><span data-stu-id="7a087-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="7a087-128">Zahrnuje také užitečné data o sadu nainstalované moduly Runtime v počítači nalezen.</span><span class="sxs-lookup"><span data-stu-id="7a087-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="7a087-129">Formát protokolu aktivace CLR není samotné popsané, ale lze použít na podporu vývojáři, kteří potřebují k vyřešení problémů aktivace CLR.</span><span class="sxs-lookup"><span data-stu-id="7a087-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a087-130">K aktivaci protokolu nelze otevřít, dokud proces, který používá modulu CLR byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="7a087-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a087-131">Protokoly aktivace CLR nejsou lokalizovány; generují se vždy v angličtině.</span><span class="sxs-lookup"><span data-stu-id="7a087-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>  
  
 <span data-ttu-id="7a087-132">V následujícím příkladu protokol aktivace je velmi užitečné informace zvýrazněnou a popsané po v protokolu.</span><span class="sxs-lookup"><span data-stu-id="7a087-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>  
  
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
  
-   <span data-ttu-id="7a087-133">**Načítání CLR protokolu** poskytuje cesta ke spustitelnému souboru, který spustil proces, který načíst spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7a087-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="7a087-134">Všimněte si, že to může být nativní hostitele.</span><span class="sxs-lookup"><span data-stu-id="7a087-134">Note that this could be a native host.</span></span>  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   <span data-ttu-id="7a087-135">**Nainstalovat modul Runtime** je sada CLR verze nainstalované v počítači, které jsou kandidáty pro žádost o aktivaci.</span><span class="sxs-lookup"><span data-stu-id="7a087-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   <span data-ttu-id="7a087-136">**vytvořená s verzí** verzi modulu CLR, který byl použit k vytvoření binárního souboru, který byl zadán pro metodu, jako je [iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="7a087-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   <span data-ttu-id="7a087-137">**Instalace funkce na vyžádání** odkazuje na povolení rozhraní .NET Framework 3.5 v systému Windows 8.</span><span class="sxs-lookup"><span data-stu-id="7a087-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="7a087-138">V tématu [rozhraní .NET Framework – chyby inicializace: Správa zkušeností uživatele](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Další informace o tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="7a087-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7a087-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a087-139">See Also</span></span>  
 [<span data-ttu-id="7a087-140">Nasazení</span><span class="sxs-lookup"><span data-stu-id="7a087-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)  
 [<span data-ttu-id="7a087-141">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5</span><span class="sxs-lookup"><span data-stu-id="7a087-141">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
