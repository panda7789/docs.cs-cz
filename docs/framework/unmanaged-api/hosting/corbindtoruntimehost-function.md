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
ms.openlocfilehash: 8c1d83b32402343f3cd2b5403e328698abd6a930
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost – funkce
Umožňuje hostitelům načíst zadaná verze modulu common language runtime (CLR) do procesu.  
  
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
 [v] Řetězec, který popisuje verzi modulu CLR, které se má zatížení.  
  
 Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí, které jsou odděleny tečkami: *major.minor.build.revision*. Řetězec předány jako `pwszVersion` musí začínat znak "v" následované první tři části číslo verze (například "v1.0.1529").  
  
 Některé verze modulu CLR jsou nainstalovány s prohlášení o zásadách, která určuje kompatibility s předchozími verzemi modulu CLR. Ve výchozím nastavení, vyhodnotí shim spuštění `pwszVersion` proti příkazy zásad a zatížením nejnovější verzi modulu runtime, je kompatibilní s požadovanou verzí. Hostitel může vynutit shim přeskočit vyhodnocení zásad a načíst přesné verze zadaná v `pwszVersion` předáním hodnoty STARTUP_LOADER_SAFEMODE pro `startupFlags` parametr.  
  
 Pokud `pwszVersion` je `null,` metodu nenačte žádné verzi modulu CLR. Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, která označuje, že se nepodařilo načíst modul runtime.  
  
 `pwszBuildFlavor`  
 [v] Řetězec, který určuje, jestli zatížení serveru nebo pracovní stanice sestavení CLR. Platné hodnoty jsou `svr` a `wks`. Sestavení serveru je optimalizovaná tak, aby využít výhod více procesorů pro kolekce a sestavení pracovní stanici je optimalizovaná pro klientské aplikace spuštěné na počítač s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načíst sestavení pracovní stanice. Při spuštění na počítač s jedním procesorem, je vždy načteno sestavení pracovní stanice, i když `pwszBuildFlavor` je nastaven na `svr`. Ale pokud `pwszBuildFlavor` je nastaven na `svr` a je zadána souběžné uvolňování (naleznete v popisu `startupFlags` parametr), je načíst sestavení serveru.  
  
> [!NOTE]
>  Souběžné uvolňování není podporována v aplikacích spuštěných WOW64 x86 emulátoru na 64bitových systémech, které implementují architektuře Intel Itanium (dříve se označovaly jako platformu IA-64). Další informace o používání WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitové aplikace](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).  
  
 `pwszHostConfigFile`  
 [v] Název konfiguračního souboru hostitele, který určuje verzi modulu CLR načíst. Pokud název souboru neobsahuje plně kvalifikovanou cestu, předpokládá se, že soubor je ve stejném adresáři jako spustitelný soubor, který je uskutečněním hovoru.  
  
 `pReserved`  
 [v] Vyhrazeno pro budoucí rozšíření.  
  
 `startupFlags`  
 [v] Sadu příznaky, které se řídí souběžné uvolňování domény neutrální kód a chování `pwszVersion` parametr. Výchozí hodnota je jedinou doménu, pokud žádné příznak nastaven. Seznam podporovaných hodnot najdete v tématu [STARTUP_FLAGS – výčet](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [v] `IID` Rozhraní jste požádali. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Ukazatel rozhraní na verzi modulu runtime, která byla načtena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
