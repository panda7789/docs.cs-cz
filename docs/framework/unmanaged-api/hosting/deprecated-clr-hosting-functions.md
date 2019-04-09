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
ms.openlocfilehash: aa84ca0defd173563817673aad183a8b64226d41
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135799"
---
# <a name="deprecated-clr-hosting-functions"></a>Zastaralé funkce hostování CLR
Tato část popisuje nespravované globální statické funkce, které používají starší verze hostujícího rozhraní API.  
  
 Kromě funkcí infrastruktury (`_Cor*` funkce), které jsou používány pouze rozhraní .NET Framework, tyto funkce se již nepoužívají v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Aktivace funkce  
 [ClrCreateManagedInstance – funkce](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Zastaralé Vytvoří instanci určeného spravovaného typu.  
  
 [CoInitializeCor – funkce](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Zastaralé. Chcete-li inicializovat common language runtime (CLR), použijte buď [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE – funkce](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Zastaralé Zajišťuje, že prováděcí modul CLR je zavedeno do procesu. Použití [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda místo.  
  
 [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Zastaralé Načte modul CLR (CLR) do procesu pomocí informací o verzi uložených v souboru XML.  
  
 [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Zastaralé Umožní nespravovaným hostitelům načíst modul CLR do procesu.  
  
 [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Zastaralé Načte modul CLR do procesu pomocí informací o verzi, která je pro čtení ze souboru XML.  
  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Zastaralé Umožňuje nespravovaným hostitelům načíst modul CLR do procesu a umožňuje nastavení příznaků, které určují chování modulu CLR.  
  
 [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Zastaralé Umožňuje hostitelům načíst zadanou verzi modulu CLR do procesu.  
  
 [GetCORRequiredVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Zastaralé Získá požadované číslo verze CLR.  
  
 [GetCORSystemDirectory – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Zastaralé Vrátí instalační adresář modulu CLR, který je načten do procesu.  
  
 [GetRealProcAddress – funkce](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Zastaralé Získá adresu zadané funkce, která je exportována z poslední instalované verzi modulu CLR.  
  
 [GetRequestedRuntimeInfo – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Zastaralé Získá informace o modulu CLR požadovaný aplikací verzi a adresář.  
  
## <a name="clr-version-functions"></a>Funkce verze CLR  
 Funkce v této části vrací verzi CLR; neaktivovat CLR.  
  
 [GetCORVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Zastaralé Vrátí číslo verze modulu CLR, na kterém běží v aktuálním procesu.  
  
 [GetFileVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Zastaralé Získá informace o verzi CLR zadaného souboru pomocí zadané vyrovnávací paměti.  
  
 [GetRequestedRuntimeVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Zastaralé Získá číslo verze modulu CLR požadované určenou aplikací. Pokud není nainstalována verze, získá nejnovější verzi, která je nainstalována před požadovanou verzí.  
  
 [GetRequestedRuntimeVersionForCLSID – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Zastaralé Získá odpovídající informace o verzi CLR pro třídu se zadaným identifikátorem CLSID.  
  
 [GetVersionFromProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Zastaralé Získá číslo verze modulu CLR, který je spojen s obslužnou rutinou určeného procesu.  
  
 [LockClrVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Zastaralé Umožňuje hostiteli zjistit, která verze modulu CLR se použije v rámci procesu před explicitní inicializací modulu CLR.  
  
## <a name="hosting-functions"></a>Funkce pro hostování  
 [CallFunctionShim – funkce](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Zastaralé Provede volání funkce, která má zadaný název a parametry v určené knihovně.  
  
 [CoEEShutDownCOM – funkce](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Zastaralé Uvolní sestavení modelu COM z procesu.  
  
 [CorExitProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Zastaralé Ukončí aktuální nespravovaný proces.  
  
 [CorLaunchApplication – funkce](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Zastaralé Spustí aplikaci v zadané síťové cestě pomocí zadaných manifestů a dalších dat aplikací.  
  
 [CorMarkThreadInThreadPool – funkce](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Zastaralé Označuje aktuálně prováděné vláken fondu vláken pro spuštění spravovaného kódu. Od verze rozhraní .NET Framework verze 2.0, tato funkce nemá žádný vliv. Není potřeba a můžete odebrat z vašeho kódu.  
  
 [CoUninitializeCor – funkce](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Zastaralé. CLR nemůže být uvolněna z procesu.  
  
 [CoUninitializeEE – funkce](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Zastaralé.  
  
 [CreateDebuggingInterfaceFromVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Zastaralé Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu na základě zadané verze informací.  
  
 [CreateICeeFileGen – funkce](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Zastaralé Vytvoří [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.  
  
 [DestroyICeeFileGen – funkce](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Zastaralé Zničí [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.  
  
 [FExecuteInAppDomainCallback – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, kterou volá CLR pro spuštění spravovaného kódu.  
  
 [FLockClrVersionCallback – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, kterou volá CLR aby upozornil hostitele, že inicializace buď zahájeno nebo dokončeno.  
  
 [GetCLRIdentityManager – funkce](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Zastaralé Získá ukazatel na rozhraní umožňující CLR spravovat identity.  
  
 [LoadLibraryShim – funkce](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Zastaralé Načte zadanou verzi knihovny DLL .NET Framework.  
  
 [LoadStringRC – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Zastaralé Převede hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.  
  
 [LoadStringRCEx – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Zastaralé Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorňuje hostitele, pokud překrytí (tj, asynchronní) vstupně-výstupních operací na zařízení byla dokončena.  
  
 [LPTHREAD_START_ROUTINE – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorňuje hostitele na spuštěný podproces ke spuštění.  
  
 [RunDll32ShimW – funkce](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Zastaralé Provede zadaný příkaz.  
  
 [WAITORTIMERCALLBACK – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorňuje hostitele, že popisovač čekání buď byl signalizován nebo vypršel časový limit.  
  
## <a name="infrastructure-functions"></a>Funkce infrastruktury  
 Funkce v této části se používají pouze rozhraní .NET Framework.  
  
 [_CorDllMain – funkce](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Inicializuje modul CLR, vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení DLL a zahájí vykonávání.  
  
 [_CorExeMain – funkce](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Inicializuje modul CLR, vyhledá spravovaný vstupní bod v záhlaví spustitelného sestavení modulu CLR a zahájí vykonávání.  
  
 [_CorExeMain2 – funkce](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Spustí vstupní bod v zadané kódu mapované paměti. Tato funkce je volána zavaděčem operačního systému.  
  
 [_CorImageUnloading – funkce](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Upozorní zavaděč na bitové kopie spravovaného modulu jsou uvolněna.  
  
 [_CorValidateImage – funkce](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Ověřuje bitové kopie spravovaného modulu a upozorní zavaděč operačního systému po jejich načtení.  
  
## <a name="see-also"></a>Viz také:

- [.NET Framework 4 – hostování globálních statických funkcí](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
