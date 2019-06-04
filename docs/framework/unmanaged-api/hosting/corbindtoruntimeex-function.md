---
title: CorBindToRuntimeEx – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b45efb634ca9b88768d6e30884085f28ad17b7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490590"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx – funkce
Umožní nespravovaným hostitelům načíst modul CLR (CLR) do procesu. [Corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) a `CorBindToRuntimeEx` funkce provádět stejnou operaci, ale `CorBindToRuntimeEx` funkce umožňuje nastavení příznaků, které určují chování modulu CLR.  
  
 Tato funkce se již nepoužívá v rozhraní .NET Framework 4.  
  
 Tato funkce přebírá sadu parametrů, které umožňují hostitele provést následující kroky:  
  
- Zadejte verzi modulu runtime, který bude načten.  
  
- Označuje, zda se mají načíst sestavení serveru nebo pracovní stanice.  
  
- Určit, jestli se provádí uvolňování paměti nebo nesouběžné uvolňování paměti.  
  
> [!NOTE]
>  Souběžné uvolňování paměti se nepodporuje v aplikacích spuštěných WOW64 x86 emulátor v 64bitových systémech, které implementují Intel Itanium architekturu (dříve označovanou jako IA-64). Další informace o použití modulu WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Řídí, zda sestavení jsou načtena jako doménově neutrální.  
  
- Získat ukazatel rozhraní k [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) , který je možné nastavit další možnosti konfigurace instance modulu CLR, před jeho spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [in] Řetězec, který popisuje verzi modulu CLR, která chcete načíst.  
  
 Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*. Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v1.0.1529").  
  
 Některé verze modulu CLR jsou nainstalovány s prohlášením o zásadách, které určuje kompatibilitu s předchozími verzemi modulu CLR. Ve výchozím nastavení překrytí spuštění vyhodnotí `pwszVersion` proti prohlášení zásad a načte nejnovější verze modulu runtime, který je kompatibilní s verzí, které jsou požadovány. Hostitel může donutit překrytí, aby přeskočilo hodnocení zásad a načetlo přesnou verzi zadané v `pwszVersion` předáním hodnoty z `STARTUP_LOADER_SAFEMODE` pro `startupFlags` parametru, jak je popsáno níže.  
  
 Pokud volající zadá hodnotu null pro `pwszVersion`, `CorBindToRuntimeEx` identifikuje sadu instalovaných modulů runtime, jejichž čísla verze nižší než modul runtime rozhraní .NET Framework 4 a načte nejnovější verzi modulu runtime z této sady. Pokud je nainstalovaná starší verze je nebude načíst rozhraní .NET Framework 4 nebo novější a selže. Všimněte si, že předávání null poskytuje hostiteli žádnou kontrolu nad tím, které je načtená verze modulu runtime. Přestože tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel zadat konkrétní verzi, kterou načíst.  
  
 `pwszBuildFlavor`  
 [in] Řetězec, který určuje, jestli se má načíst server nebo pracovní stanice sestavení CLR. Platné hodnoty jsou `svr` a `wks`. Sestavení serveru je optimalizováno pro využití více procesorů pro uvolňování paměti kolekce a sestavení pracovní stanice je optimalizována pro klientské aplikace spuštěné v počítači s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastavena na hodnotu null, je načteno sestavení pracovní stanice. Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno, i když `pwszBuildFlavor` je nastavena na `svr`. Ale pokud `pwszBuildFlavor` je nastavena na `svr` a souběžné uvolňování je vyznačeno (viz popis `startupFlags` parametr), načte se sestavení serveru.  
  
 `startupFlags`  
 [in] Kombinace hodnot, které [startup_flags –](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu. Tyto příznaky řídí souběžné uvolňování paměti, doménově neutrální kód a chování `pwszVersion` parametru. Pokud není nastaven žádný příznak, výchozí hodnota je jedinou doménu. Platné jsou následující hodnoty:  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 Popisy těchto příznaků, najdete v článku [startup_flags –](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.  
  
 `rclsid`  
 [in] `CLSID` Třídy typu coclass, která implementuje [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] `IID` Požadovaná rozhraní z `rclsid`. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Vrácený ukazatel rozhraní k `riid`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pwszVersion` Určuje verzi modulu runtime, který neexistuje, `CorBindToRuntimeEx` vrátí CLR_E_SHIM_RUNTIMELOAD hodnotu HRESULT.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontext spuštění a tok Windows Identity  
 V modulu CLR verze 1 <xref:System.Security.Principal.WindowsIdentity> objektu není téct přes asynchronní body jako nová vlákna, fondy vláken nebo zpětná volání časovače. V modulu CLR verze 2.0 <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěné vlákno a toky ji napříč asynchronní čárky, ale ne přes hranice aplikačních domén. Podobně platí <xref:System.Security.Principal.WindowsIdentity> objekt také průchodu čárky asynchronní. Proto aktuální zosobnění ve vlákně, pokud existuje, toky příliš.  
  
 Je možné změnit toku dvěma způsoby:  
  
1. Úpravou <xref:System.Threading.ExecutionContext> nastavení potlačení toku na základě vlákno (najdete v článku <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).  
  
2. Změnou výchozí režim procesu na režim kompatibility verze 1, kde <xref:System.Security.Principal.WindowsIdentity> objektu není téct přes asynchronní fázi bez ohledu na to <xref:System.Threading.ExecutionContext> nastavení pro aktuální vlákno. Jak změnit výchozí režim závisí na, jestli používat spravované spustitelný soubor nebo nespravovaných hostitelských rozhraní načíst modul CLR:  
  
    1. Pro spravované spustitelné soubory, je nutné nastavit `enabled` atribut [ \<legacyimpersonationpolicy – >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.  
  
    2. Pro nespravovaná rozhraní pro hostování, nastavit `STARTUP_LEGACY_IMPERSONATION` příznak v `startupFlags` parametru při volání `CorBindToRuntimeEx` funkce.  
  
     Režim kompatibility verze 1 platí pro celý proces a všech doménách aplikace v procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
