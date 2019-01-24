---
title: CorBindToRuntimeHost – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c65b0f2b91527d7cd2c1ef2eba607bbd477571e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699451"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost – funkce
Umožňuje hostitelům načíst zadanou verzi modulu common language runtime (CLR) do procesu.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [in] Řetězec, který popisuje verzi modulu CLR, který chcete načíst.  
  
 Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*. Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v1.0.1529").  
  
 Některé verze modulu CLR jsou nainstalovány s prohlášením o zásadách, které určuje kompatibilitu s předchozími verzemi modulu CLR. Ve výchozím nastavení překrytí spuštění vyhodnotí `pwszVersion` proti prohlášení zásad a načte nejnovější verze modulu runtime, který je kompatibilní s verzí, které jsou požadovány. Hostitel může donutit překrytí, aby přeskočilo hodnocení zásad a načetlo přesnou verzi zadané v `pwszVersion` předáním hodnoty startup_loader_safemode pro `startupFlags` parametru.  
  
 Pokud `pwszVersion` je `null,` metoda nenačte žádné verzi modulu CLR. Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, což znamená, že se nezdařilo načtení modulu runtime.  
  
 `pwszBuildFlavor`  
 [in] Řetězec, který určuje, jestli se má načíst server nebo pracovní stanice sestavení CLR. Platné hodnoty jsou `svr` a `wks`. Sestavení serveru je optimalizováno pro využití více procesorů pro uvolňování paměti kolekce a sestavení pracovní stanice je optimalizována pro klientské aplikace spuštěné v počítači s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastavena na hodnotu null, je načteno sestavení pracovní stanice. Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno, i když `pwszBuildFlavor` je nastavena na `svr`. Ale pokud `pwszBuildFlavor` je nastavena na `svr` a souběžné uvolňování je vyznačeno (viz popis `startupFlags` parametr), načte se sestavení serveru.  
  
> [!NOTE]
>  Souběžné uvolňování paměti se nepodporuje v aplikacích spuštěných WOW64 x86 emulátor v 64bitových systémech, které implementují Intel Itanium architekturu (dříve označovanou jako IA-64). Další informace o použití modulu WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 [in] Název konfiguračního souboru hostitele, který určuje verzi modulu CLR pro načtení. Pokud název souboru neobsahuje úplnou cestu, soubor je považován za ve stejném adresáři jako spustitelný soubor, který provádí volání.  
  
 `pReserved`  
 [in] Vyhrazeno pro budoucí rozšíření.  
  
 `startupFlags`  
 [in] Sada příznaků, které řídí souběžné uvolňování paměti, doménově neutrální kód a chování `pwszVersion` parametru. Pokud není nastaven žádný příznak, výchozí hodnota je jedinou doménu. Seznam podporovaných hodnot naleznete v tématu [startup_flags – výčet](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [in] `CLSID` Třídy typu coclass, která implementuje [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] `IID` Rozhraní, které jste požádali. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Ukazatel rozhraní na verzi modulu runtime, který byl načten.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
