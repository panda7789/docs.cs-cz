---
title: Zastaralé funkce hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d86f9b4903663604094895f6747b1407ff98c990
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435861"
---
# <a name="deprecated-clr-hosting-functions"></a>Zastaralé funkce hostování CLR
Tato část popisuje nespravované globální statické funkce, které používají starší verze hostování rozhraní API.  
  
 S výjimkou funkcí infrastruktury (`_Cor*` funkce), které jsou používány pouze rozhraní .NET Framework, tyto funkce jsou zastaralé v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Aktivace funkce  
 [ClrCreateManagedInstance – funkce](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Zastaralé Vytvoří instanci je určeného spravovaného typu.  
  
 [CoInitializeCor – funkce](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Zastaralé. Chcete-li inicializovat modul CLR (CLR), použijte buď [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE – funkce](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Zastaralé Zajišťuje, že je modul CLR provádění načtena do procesu. Použití [iclrruntimehost::Start –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda místo.  
  
 [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Zastaralé Načte modul CLR (CLR) do procesu pomocí verze informace uložené v souboru XML.  
  
 [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Zastaralé Umožňuje nespravované hostitelé načíst modul CLR do procesu.  
  
 [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Zastaralé Načte modul CLR do procesu pomocí informací o verzi, která je pro čtení ze souboru XML.  
  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Zastaralé Umožňuje načíst modul CLR do procesu nespravované hostitelům a umožňuje nastavit příznaky určit způsob chování modulu CLR.  
  
 [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Zastaralé Umožňuje hostitelům načíst zadaná verze modulu CLR do procesu.  
  
 [GetCORRequiredVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Zastaralé Získá požadované číslo verze CLR.  
  
 [GetCORSystemDirectory – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Zastaralé Vrátí instalační adresář modulu CLR, který je načten do procesu.  
  
 [GetRealProcAddress – funkce](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Zastaralé Získá adresu zadaná funkce, který je exportován z nainstalované verze modulu CLR.  
  
 [GetRequestedRuntimeInfo – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Zastaralé Získá informace o modulu CLR požadoval aplikace verzi a adresáře.  
  
## <a name="clr-version-functions"></a>Funkce verze CLR  
 Funkce v této části vrátit verze CLR; Neaktivujte modulu CLR.  
  
 [GetCORVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Zastaralé Vrátí číslo verze modulu CLR, který běží v aktuálním procesu.  
  
 [GetFileVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Zastaralé Získá informace o verzi CLR zadaného souboru, pomocí zadané vyrovnávací paměti.  
  
 [GetRequestedRuntimeVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Zastaralé Získá číslo verze modulu CLR požadoval zadané aplikace. Pokud není nainstalovaná této verze, získá nejnovější verzi, který se nainstaloval před požadovanou verzi.  
  
 [GetRequestedRuntimeVersionForCLSID – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Zastaralé Získá příslušné informace verze CLR pro třídu s zadaný CLSID.  
  
 [GetVersionFromProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Zastaralé Získá číslo verze modulu CLR, která souvisí s popisovačem určený proces.  
  
 [LockClrVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Zastaralé Umožňuje hostiteli, chcete-li zjistit, kterou verzi modulu CLR se použije v procesu před explicitně inicializace modulu CLR.  
  
## <a name="hosting-functions"></a>Hostování funkcí  
 [CallFunctionShim – funkce](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Zastaralé Zavolá funkci, která má zadaný název a parametry v určené knihovně.  
  
 [CoEEShutDownCOM – funkce](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Zastaralé Uvolní sestavení modelu COM z procesu.  
  
 [CorExitProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Zastaralé Ukončí proces aktuální nespravované.  
  
 [CorLaunchApplication – funkce](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Zastaralé Spuštění aplikace v zadané síťové cestě, pomocí zadané manifesty a ostatní data aplikací.  
  
 [CorMarkThreadInThreadPool – funkce](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Zastaralé Označí aktuálně prováděné vlákno fondu vláken pro spuštění spravovaného kódu. Od verze rozhraní .NET Framework verze 2.0, tato funkce nemá žádný vliv. Není nutné a může být odebrán z vašeho kódu.  
  
 [CoUninitializeCor – funkce](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Zastaralé. Modul CLR nemůže být uvolněna z procesu.  
  
 [CoUninitializeEE – funkce](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Zastaralé.  
  
 [CreateDebuggingInterfaceFromVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Zastaralé Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objekt založený na informacích zadaná verze.  
  
 [CreateICeeFileGen – funkce](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Zastaralé Vytvoří [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.  
  
 [DestroyICeeFileGen – funkce](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Zastaralé Zničí [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.  
  
 [FExecuteInAppDomainCallback – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která volá modulu CLR provést spravovaného kódu.  
  
 [FLockClrVersionCallback – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která volá modulu CLR oznámit hostitele tohoto inicializace má buď spustit nebo byla dokončena.  
  
 [GetCLRIdentityManager – funkce](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Zastaralé Získá ukazatel na rozhraní, které umožňuje spravovat identity modulu CLR.  
  
 [LoadLibraryShim – funkce](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Zastaralé Načte zadaný verzi knihovny DLL rozhraní .NET Framework.  
  
 [LoadStringRC – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Zastaralé Změní hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.  
  
 [LoadStringRCEx – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Zastaralé Přeloží hodnotou HRESULT odpovídající chybové zprávy pro zadanou jazykovou verzi.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorní hostitele, když překryté (tedy asynchronní) vstupně-výstupních operací na zařízení byla dokončena.  
  
 [LPTHREAD_START_ROUTINE – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorní hostitele, který spustil vlákno k provedení.  
  
 [RunDll32ShimW – funkce](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Zastaralé Provede zadaný příkaz.  
  
 [WAITORTIMERCALLBACK – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorní hostitele, že popisovač čekání buď byla signál nebo vypršel časový limit.  
  
## <a name="infrastructure-functions"></a>Funkce infrastruktury  
 Funkce v této části jsou pro použití v rozhraní .NET Framework.  
  
 [_CorDllMain – funkce](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Inicializuje modulu CLR, vyhledá spravované vstupní bod v záhlaví modulu CLR sestavení knihoven DLL a zahájí spuštění.  
  
 [_CorExeMain – funkce](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Inicializuje modulu CLR, vyhledá spravované vstupní bod v záhlaví modulu CLR spustitelný soubor sestavení a zahájí spuštění.  
  
 [_CorExeMain2 – funkce](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Vstupní bod se spustí v zadaný kód mapované paměti. Tato funkce je volána zavaděčem operačního systému.  
  
 [_CorImageUnloading – funkce](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Zavaděč upozorní, když jsou obrázky spravovaný modul odpojen.  
  
 [_CorValidateImage – funkce](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Ověří spravovaný modul bitové kopie a po nějaké době načíst upozorní zavaděč operačního systému.  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce .NET Framework 4 pro hostování](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
