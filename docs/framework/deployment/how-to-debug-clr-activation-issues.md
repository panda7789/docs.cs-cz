---
title: 'Postupy: Ladění problémů aktivace CLR'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b78d917b95e06a14b74c812bf92107476ad17212
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-debug-clr-activation-issues"></a>Postupy: Ladění problémů aktivace CLR
Pokud narazíte na potíže při získávání aplikace na spouštění se správnou verzí common language runtime (CLR), můžete zobrazit a ladění protokoly aktivace CLR. Tyto protokoly může být velmi užitečná při určení příčiny problému aktivace, když aplikace načte různé verze CLR, než se očekávalo nebo vůbec nenačte modulu CLR. [Rozhraní .NET Framework – chyby inicializace: Správa uživatelské prostředí](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) popisuje možnosti, když se najde žádné CLR pro aplikaci.  
  
 Protokolování aktivace CLR může být povoleno systémové pomocí klíče registru HKEY_LOCAL_MACHINE nebo systémové proměnné prostředí. V protokolu se budou generovat dokud položku registru nebo proměnná prostředí je odebrat. Alternativně můžete použít na uživatele nebo proměnná prostředí místní proces povolení protokolování s jiný rozsah a doba trvání.  
  
 Protokoly aktivace CLR Nezaměňovat s [sestavení – vazby protokolů](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), který se zcela liší.  
  
## <a name="to-enable-clr-activation-logging"></a>Chcete-li povolit protokolování aktivace CLR  
  
#### <a name="using-the-registry"></a>Pomocí klíče registru  
  
1.  V editoru registru přejděte na HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (v počítači 32bitová verze) nebo HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Složka NETFramework (na 64bitovém počítači).  
  
2.  Přidejte řetězcovou hodnotu s názvem `CLRLoadLogDir`a nastavte ji na úplnou cestu existující adresář kam chcete ukládat aktivační události CLR.  
  
 Aktivace protokolování byla povolena, dokud neodeberete hodnotu řetězce.  
  
#### <a name="using-an-environment-variable"></a>Pomocí proměnné prostředí  
  
-   Nastavte `COMPLUS_CLRLoadLogDir` proměnnou prostředí na řetězec, který představuje úplnou cestu existující adresář, kam chcete ukládat aktivační události CLR.  
  
     Určuje, jak nastavit proměnnou prostředí svém oboru:  
  
    -   Pokud je nastavena na úrovni systému, aktivace protokolování je povoleno pro všechny aplikace rozhraní .NET Framework na tomto počítači, dokud se neodstraní proměnnou prostředí.  
  
    -   Pokud je nastavena na úrovni uživatele, aktivaci protokolování je povolená jenom pro aktuální uživatelský účet. Protokolování bude pokračovat, dokud se neodstraní proměnné prostředí.  
  
    -   Pokud jste nastavili z v rámci procesu před načtením modulu CLR, je povoleno protokolování aktivace, dokud se proces ukončí.  
  
    -   Pokud je nastavena na příkazovém řádku před spuštěním aplikace, je povoleno protokolování aktivace pro každou aplikaci, která se spouští z tohoto příkazového řádku.  
  
     Například k ukládání protokolů aktivace v adresáři c:\clrloadlogs proces úrovni oboru, otevřete okno příkazového řádku a zadejte následující příkaz před spuštěním aplikace:  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a>Příklad  
 Protokoly aktivace CLR poskytují velké množství dat o CLR – aktivace a použití modulu CLR hostování rozhraní API. Většina těchto dat se používá interně společností Microsoft, ale některá data může být také užitečné pro vývojáře, jak je popsáno v tomto článku.  
  
 Protokol odráží pořadí, v jakém modul CLR, který je hostitelem rozhraní API byla volána. Zahrnuje také užitečné data o sadu nainstalované moduly Runtime v počítači nalezen. Formát protokolu aktivace CLR není samotné popsané, ale lze použít na podporu vývojáři, kteří potřebují k vyřešení problémů aktivace CLR.  
  
> [!NOTE]
>  K aktivaci protokolu nelze otevřít, dokud proces, který používá modulu CLR byl ukončen.  
  
> [!NOTE]
>  Protokoly aktivace CLR nejsou lokalizovány; generují se vždy v angličtině.  
  
 V následujícím příkladu protokol aktivace je velmi užitečné informace zvýrazněnou a popsané po v protokolu.  
  
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
  
-   **Načítání CLR protokolu** poskytuje cesta ke spustitelnému souboru, který spustil proces, který načíst spravovaného kódu. Všimněte si, že to může být nativní hostitele.  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   **Nainstalovat modul Runtime** je sada CLR verze nainstalované v počítači, které jsou kandidáty pro žádost o aktivaci.  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   **vytvořená s verzí** verzi modulu CLR, který byl použit k vytvoření binárního souboru, který byl zadán pro metodu, jako je [iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   **Instalace funkce na vyžádání** odkazuje na povolení rozhraní .NET Framework 3.5 v systému Windows 8. V tématu [rozhraní .NET Framework – chyby inicializace: Správa zkušeností uživatele](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) Další informace o tomto scénáři.  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Nasazení](../../../docs/framework/deployment/index.md)  
 [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
