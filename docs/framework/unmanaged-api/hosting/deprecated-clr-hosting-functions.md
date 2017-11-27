---
title: "Zastaralé funkce hostování CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a>Zastaralé funkce hostování CLR
Tato část popisuje nespravované globální statické funkce, které používají starší verze hostování rozhraní API.  
  
 S výjimkou funkcí infrastruktury (`_Cor*` funkce), které jsou používány pouze rozhraní .NET Framework, tyto funkce jsou zastaralé v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Aktivace funkce  
 [Clrcreatemanagedinstance – funkce](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Zastaralé Vytvoří instanci je určeného spravovaného typu.  
  
 [Coinitializecor – funkce](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Zastaralé. Chcete-li inicializovat modul CLR (CLR), použijte buď [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [Coinitializeee – funkce](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Zastaralé Zajišťuje, že je modul CLR provádění načtena do procesu. Použití [iclrruntimehost::Start –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda místo.  
  
 [Corbindtocurrentruntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Zastaralé Načte modul CLR (CLR) do procesu pomocí verze informace uložené v souboru XML.  
  
 [Corbindtoruntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Zastaralé Umožňuje nespravované hostitelé načíst modul CLR do procesu.  
  
 [Corbindtoruntimebycfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Zastaralé Načte modul CLR do procesu pomocí informací o verzi, která je pro čtení ze souboru XML.  
  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Zastaralé Umožňuje načíst modul CLR do procesu nespravované hostitelům a umožňuje nastavit příznaky určit způsob chování modulu CLR.  
  
 [Corbindtoruntimehost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Zastaralé Umožňuje hostitelům načíst zadaná verze modulu CLR do procesu.  
  
 [Getcorrequiredversion – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Zastaralé Získá požadované číslo verze CLR.  
  
 [Getcorsystemdirectory – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Zastaralé Vrátí instalační adresář modulu CLR, který je načten do procesu.  
  
 [Getrealprocaddress – funkce](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Zastaralé Získá adresu zadaná funkce, který je exportován z nainstalované verze modulu CLR.  
  
 [Getrequestedruntimeinfo – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Zastaralé Získá informace o modulu CLR požadoval aplikace verzi a adresáře.  
  
## <a name="clr-version-functions"></a>Funkce verze CLR  
 Funkce v této části vrátit verze CLR; Neaktivujte modulu CLR.  
  
 [Getcorversion – funkce](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Zastaralé Vrátí číslo verze modulu CLR, který běží v aktuálním procesu.  
  
 [Getfileversion – funkce](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Zastaralé Získá informace o verzi CLR zadaného souboru, pomocí zadané vyrovnávací paměti.  
  
 [Getrequestedruntimeversion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Zastaralé Získá číslo verze modulu CLR požadoval zadané aplikace. Pokud není nainstalovaná této verze, získá nejnovější verzi, který se nainstaloval před požadovanou verzi.  
  
 [Getrequestedruntimeversionforclsid – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Zastaralé Získá příslušné informace verze CLR pro třídu s zadaný CLSID.  
  
 [Getversionfromprocess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Zastaralé Získá číslo verze modulu CLR, která souvisí s popisovačem určený proces.  
  
 [Lockclrversion – funkce](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Zastaralé Umožňuje hostiteli, chcete-li zjistit, kterou verzi modulu CLR se použije v procesu před explicitně inicializace modulu CLR.  
  
## <a name="hosting-functions"></a>Hostování funkcí  
 [Callfunctionshim – funkce](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Zastaralé Zavolá funkci, která má zadaný název a parametry v určené knihovně.  
  
 [Coeeshutdowncom – funkce](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Zastaralé Uvolní sestavení modelu COM z procesu.  
  
 [Corexitprocess – funkce](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Zastaralé Ukončí proces aktuální nespravované.  
  
 [Corlaunchapplication – funkce](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Zastaralé Spuštění aplikace v zadané síťové cestě, pomocí zadané manifesty a ostatní data aplikací.  
  
 [Cormarkthreadinthreadpool – funkce](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Zastaralé Označí aktuálně prováděné vlákno fondu vláken pro spuštění spravovaného kódu. Od verze rozhraní .NET Framework verze 2.0, tato funkce nemá žádný vliv. Není nutné a může být odebrán z vašeho kódu.  
  
 [Couninitializecor – funkce](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Zastaralé. Modul CLR nemůže být uvolněna z procesu.  
  
 [Couninitializeee – funkce](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Zastaralé.  
  
 [Createdebugginginterfacefromversion – funkce](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Zastaralé Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objekt založený na informacích zadaná verze.  
  
 [Createiceefilegen – funkce](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Zastaralé Vytvoří [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.  
  
 [Destroyiceefilegen – funkce](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Zastaralé Zničí [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.  
  
 [Ukazatel na funkci FExecuteInAppDomainCallback](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která volá modulu CLR provést spravovaného kódu.  
  
 [Ukazatel na funkci FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která volá modulu CLR oznámit hostitele tohoto inicializace má buď spustit nebo byla dokončena.  
  
 [Getclridentitymanager – funkce](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Zastaralé Získá ukazatel na rozhraní, které umožňuje spravovat identity modulu CLR.  
  
 [LoadLibraryShim – funkce](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Zastaralé Načte zadaný verzi knihovny DLL rozhraní .NET Framework.  
  
 [Loadstringrc – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Zastaralé Změní hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.  
  
 [Loadstringrcex – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Zastaralé Přeloží hodnotou HRESULT odpovídající chybové zprávy pro zadanou jazykovou verzi.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorní hostitele, když překryté (tedy asynchronní) vstupně-výstupních operací na zařízení byla dokončena.  
  
 [LPTHREAD_START_ROUTINE – ukazatel na funkci](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorní hostitele, který spustil vlákno k provedení.  
  
 [Rundll32shimw – funkce](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Zastaralé Provede zadaný příkaz.  
  
 [Waitortimercallback – ukazatel funkce](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Zastaralé Odkazuje na funkci, která upozorní hostitele, že popisovač čekání buď byla signál nebo vypršel časový limit.  
  
## <a name="infrastructure-functions"></a>Funkce infrastruktury  
 Funkce v této části jsou pro použití v rozhraní .NET Framework.  
  
 [_CorDllMain – funkce](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Inicializuje modulu CLR, vyhledá spravované vstupní bod v záhlaví modulu CLR sestavení knihoven DLL a zahájí spuštění.  
  
 [_CorExeMain – funkce](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Inicializuje modulu CLR, vyhledá spravované vstupní bod v záhlaví modulu CLR spustitelný soubor sestavení a zahájí spuštění.  
  
 [_Corexemain2 – funkce](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Vstupní bod se spustí v zadaný kód mapované paměti. Tato funkce je volána zavaděčem operačního systému.  
  
 [_CorImageUnloading – funkce](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Zavaděč upozorní, když jsou obrázky spravovaný modul odpojen.  
  
 [_CorValidateImage – funkce](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Ověří spravovaný modul bitové kopie a po nějaké době načíst upozorní zavaděč operačního systému.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní .NET framework 4 – hostování globálních statických funkcí](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
