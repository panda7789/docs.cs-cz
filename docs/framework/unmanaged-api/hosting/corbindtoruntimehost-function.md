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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176484"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost – funkce
Umožňuje hostitelům načíst zadanou verzi běžného jazykového běhu (CLR) do procesu.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [v] Řetězec, který popisuje verzi CLR, kterou chcete načíst.  
  
 Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*. Řetězec předán `pwszVersion` jako musí začínat znak "v" následuje první tři části číslo verze (například "v1.0.1529").  
  
 Některé verze clr jsou nainstalovány s prohlášením zásad, které určuje kompatibilitu s předchozími verzemi CLR. Ve výchozím nastavení překrytí `pwszVersion` při spuštění vyhodnocuje příkazy zásad a načte nejnovější verzi běhu, který je kompatibilní s požadovanou verzí. Hostitel může vynutit překrytí přeskočit vyhodnocení zásad a `pwszVersion` načíst přesnou verzi `startupFlags` zadanou v souboru předáním hodnoty STARTUP_LOADER_SAFEMODE parametru.  
  
 Pokud `pwszVersion` `null,` je metoda nenačte žádnou verzi CLR. Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, což znamená, že se nepodařilo načíst za běhu.  
  
 `pwszBuildFlavor`  
 [v] Řetězec, který určuje, zda má být server nebo sestavení pracovní stanice CLR načíst. Platné hodnoty `svr` `wks`jsou a . Sestavení serveru je optimalizováno tak, aby využívalo více procesorů pro uvolňování paměti, a sestavení pracovní stanice je optimalizováno pro klientské aplikace spuštěné v počítači s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastavena na hodnotu null, sestavení pracovní stanice je načten. Při spuštění na počítači s jedním procesorem je sestavení `pwszBuildFlavor` pracovní `svr`stanice vždy načteno, i když je nastaveno na . Však `pwszBuildFlavor` pokud je `svr` nastavena a souběžné uvolňování paměti `startupFlags` je zadán (viz popis parametru), sestavení serveru je načten.  
  
> [!NOTE]
> Souběžné uvolňování paměti není podporováno v aplikacích se systémem WOW64 x86 emulátoru na 64bitové systémy, které implementují architekturu Intel Itanium (dříve nazývané IA-64). Další informace o používání wow64 v 64bitových systémech Windows naleznete v [tématu Spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 [v] Název konfiguračního souboru hostitele, který určuje verzi clr načíst. Pokud název souboru neobsahuje plně kvalifikovanou cestu, předpokládá se, že soubor je ve stejném adresáři jako spustitelný soubor, který provádí volání.  
  
 `pReserved`  
 [v] Vyhrazeno pro budoucí rozšiřitelnost.  
  
 `startupFlags`  
 [v] Sada příznaků, která řídí souběžné uvolňování paměti, kód neutrální `pwszVersion` z domény a chování parametru. Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak. Seznam podporovaných hodnot naleznete ve [STARTUP_FLAGS výčtu](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [v] Coclass, `CLSID` která implementuje buď [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [v] Rozhraní, `IID` které požadujete. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Ukazatel rozhraní na verzi modulu runtime, který byl načten.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** Soubor MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
