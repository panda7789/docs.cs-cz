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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176497"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx – funkce
Umožňuje nespravovaným hostitelům načíst běžný jazyk runtime (CLR) do procesu. [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) a `CorBindToRuntimeEx` funkce provádět stejnou operaci, ale `CorBindToRuntimeEx` funkce umožňuje nastavit příznaky určit chování CLR.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
 Tato funkce přebírá sadu parametrů, které umožňují hostiteli provést následující akce:  
  
- Zadejte verzi runtime, která bude načtena.  
  
- Určete, zda má být načteno sestavení serveru nebo pracovní stanice.  
  
- Určit, zda je provedeno souběžné uvolňování paměti nebo nesouběžné uvolňování paměti.  
  
> [!NOTE]
> Souběžné uvolňování paměti není podporováno v aplikacích se systémem WOW64 x86 emulátoru na 64bitové systémy, které implementují architekturu Intel Itanium (dříve nazývané IA-64). Další informace o používání wow64 v 64bitových systémech Windows naleznete v [tématu Spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Určit, zda sestavení jsou načteny jako neutrální domény.  
  
- Získejte ukazatel rozhraní na [ICorRuntimeHost,](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) který lze použít k nastavení dalších možností pro konfiguraci instance CLR před jejím spuštěním.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [v] Řetězec popisující verzi CLR, kterou chcete načíst.  
  
 Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*. Řetězec předán `pwszVersion` jako musí začínat znak "v" následuje první tři části číslo verze (například "v1.0.1529").  
  
 Některé verze clr jsou nainstalovány s prohlášením zásad, které určuje kompatibilitu s předchozími verzemi CLR. Ve výchozím nastavení překrytí `pwszVersion` při spuštění vyhodnocuje příkazy zásad a načte nejnovější verzi běhu, který je kompatibilní s požadovanou verzí. Hostitel může vynutit překrytí přeskočit vyhodnocení zásad a `pwszVersion` načíst přesnou `startupFlags` verzi zadanou v souboru předáním hodnoty parametru, `STARTUP_LOADER_SAFEMODE` jak je popsáno níže.  
  
 Pokud volající určuje hodnotu null for `pwszVersion`, `CorBindToRuntimeEx` identifikuje sadu nainstalovaných runtime, jejichž čísla verzí jsou nižší než runtime rozhraní .NET Framework 4, a načte nejnovější verzi runtime z této sady. Nenačte rozhraní .NET Framework 4 nebo novější a selže, pokud není nainstalována žádná starší verze. Všimněte si, že předávání null dává hostiteli žádnou kontrolu nad tím, která verze runtime je načten. Ačkoli tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel dodat konkrétní verzi načíst.  
  
 `pwszBuildFlavor`  
 [v] Řetězec, který určuje, zda má být server nebo sestavení pracovní stanice CLR načíst. Platné hodnoty `svr` `wks`jsou a . Sestavení serveru je optimalizováno tak, aby využívalo více procesorů pro uvolňování paměti, a sestavení pracovní stanice je optimalizováno pro klientské aplikace spuštěné v počítači s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastavena na hodnotu null, sestavení pracovní stanice je načten. Při spuštění na počítači s jedním procesorem je sestavení `pwszBuildFlavor` pracovní `svr`stanice vždy načteno, i když je nastaveno na . Však `pwszBuildFlavor` pokud je `svr` nastavena a souběžné uvolňování paměti `startupFlags` je zadán (viz popis parametru), sestavení serveru je načten.  
  
 `startupFlags`  
 [v] Kombinace hodnot [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu. Tyto příznaky řídí souběžné uvolňování paměti, kód neutrální `pwszVersion` z domény a chování parametru. Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak. Následující hodnoty jsou platné:  
  
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
  
 Popis těchto příznaků naleznete ve [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu.  
  
 `rclsid`  
 [v] Coclass, `CLSID` která implementuje buď [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [v] Požadované `IID` rozhraní od `rclsid`aplikace . Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Vrácený ukazatel `riid`rozhraní na .  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pwszVersion` určuje verzi runtime, která `CorBindToRuntimeEx` neexistuje, vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontext spuštění a tok identity systému Windows  
 Ve verzi 1 CLR <xref:System.Security.Principal.WindowsIdentity> objekt netokuje přes asynchronní body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače. Ve verzi 2.0 CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěném vlákně a nateče přes libovolný asynchronní bod, ale ne přes hranice domény aplikace. Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také toky přes všechny asynchronní bod. Proto aktuální zosobnění ve vlákně, pokud existuje, toky příliš.  
  
 Tok můžete změnit dvěma způsoby:  
  
1. Úpravou <xref:System.Threading.ExecutionContext> nastavení potlačit tok na základě vlákno (viz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> , a metody).  
  
2. Změnou výchozího režimu procesu na režim <xref:System.Security.Principal.WindowsIdentity> kompatibility verze 1, kde objekt neprobíhá <xref:System.Threading.ExecutionContext> přes žádný asynchronní bod, bez ohledu na nastavení v aktuálním vlákně. Způsob změny výchozího režimu závisí na tom, zda k načtení příkazu CLR načtete spravované spustitelné nebo nespravované hostitelské rozhraní:  
  
    1. U spravovaných spustitelných `enabled` souborů je nutné nastavit atribut [ \<staršího prvku ImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true`.  
  
    2. Pro nespravované hostitelské rozhraní `STARTUP_LEGACY_IMPERSONATION` nastavte příznak `startupFlags` v parametru při volání `CorBindToRuntimeEx` funkce.  
  
     Režim kompatibility verze 1 se vztahuje na celý proces a na všechny aplikační domény v procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Soubor MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
