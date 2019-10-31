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
ms.openlocfilehash: 794a39f1e2c4a93a34ae39641519c79fd4c4e79e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131230"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx – funkce
Umožňuje nespravovaným hostitelům načíst modul CLR (Common Language Runtime) do procesu. Funkce [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) a `CorBindToRuntimeEx` provádí stejnou operaci, ale funkce `CorBindToRuntimeEx` umožňuje nastavit příznaky pro určení chování modulu CLR.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
 Tato funkce přijímá sadu parametrů, které umožní hostiteli provést následující akce:  
  
- Zadejte verzi modulu runtime, který bude načten.  
  
- Označuje, zda má být načteno sestavení serveru nebo pracovní stanice.  
  
- Určuje, zda je provedeno souběžné uvolňování paměti nebo nesouběžné uvolňování paměti.  
  
> [!NOTE]
> Souběžné uvolňování paměti není podporováno v aplikacích spouštějících emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64). Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Určete, zda jsou sestavení načtena jako doménově neutrální.  
  
- Získejte ukazatel rozhraní na [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) , který lze použít k nastavení dalších možností konfigurace instance CLR před jeho spuštěním.  
  
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
 pro Řetězec popisující verzi modulu CLR, kterou chcete načíst.  
  
 Číslo verze v .NET Framework se skládá ze čtyř částí oddělených tečkami: *hlavní_verze. podverze. sestavení. revize*. Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v 1.0.1529").  
  
 Některé verze modulu CLR jsou nainstalovány s příkazem zásad, který určuje kompatibilitu s předchozími verzemi modulu CLR. Ve výchozím nastavení překrytí po spuštění vyhodnocuje `pwszVersion` proti příkazům zásad a načte nejnovější verzi modulu runtime, která je kompatibilní s požadovanou verzí. Hostitel může vynutit překrytí, aby přeskočil vyhodnocení zásad a načetlo přesnou verzi určenou v `pwszVersion` předáním hodnoty `STARTUP_LOADER_SAFEMODE` parametru `startupFlags`, jak je popsáno níže.  
  
 Pokud volající pro `pwszVersion`zadá hodnotu null, `CorBindToRuntimeEx` identifikuje sadu nainstalovaných modulů runtime, jejichž čísla verzí jsou nižší než modul runtime .NET Framework 4, a načte nejnovější verzi modulu runtime z této sady. Nenačte .NET Framework 4 nebo novější a neproběhne úspěšně, pokud není nainstalovaná žádná starší verze. Všimněte si, že předání hodnoty null dává hostiteli žádnou kontrolu nad tím, která verze modulu runtime je načtena. I když tento přístup může být v některých scénářích vhodný, důrazně doporučujeme, aby hostitel zadal konkrétní verzi, která se má načíst.  
  
 `pwszBuildFlavor`  
 pro Řetězec, který určuje, zda má být načten Server nebo pracovní stanice sestavení modulu CLR. Platné hodnoty jsou `svr` a `wks`. Sestavení serveru je optimalizované tak, aby využívalo více procesorů pro uvolňování paměti a aby bylo sestavení pracovní stanice optimalizované pro klientské aplikace běžící na počítači s jedním procesorem.  
  
 Pokud je `pwszBuildFlavor` nastaveno na hodnotu null, je načteno sestavení pracovní stanice. Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno, i když je `pwszBuildFlavor` nastaveno na `svr`. Pokud je však `pwszBuildFlavor` nastavena na `svr` a je-li zadáno souběžné uvolňování paměti (viz popis `startupFlags` parametr), je sestavení serveru načteno.  
  
 `startupFlags`  
 pro Kombinace hodnot výčtu [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) . Tyto příznaky řídí souběžné uvolňování paměti, doménový neutrální kód a chování parametru `pwszVersion`. Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak. Platné jsou následující hodnoty:  
  
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
  
 Popisy těchto příznaků naleznete v tématu výčet [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .  
  
 `rclsid`  
 pro `CLSID` třídy coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) . Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 pro `IID` z vyžádaného rozhraní z `rclsid`. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 mimo Vrácený ukazatel rozhraní na `riid`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pwszVersion` určuje verzi modulu runtime, která neexistuje, `CorBindToRuntimeEx` vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontext spuštění a tok identity Windows  
 Ve verzi 1 modulu CLR objekt <xref:System.Security.Principal.WindowsIdentity> neprovádí tok mezi asynchronními body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače. Ve verzi 2,0 CLR objekt <xref:System.Threading.ExecutionContext> zalomí některé informace o aktuálně zpracovávaném vlákně a natéká ho napříč jakýmkoli asynchronním bodem, ale ne napříč hranicemi aplikační domény. Podobně objekt <xref:System.Security.Principal.WindowsIdentity> také toků napříč jakýmkoli asynchronním bodem. Proto aktuální zosobnění ve vlákně, pokud nějaký existuje, je také toků.  
  
 Tok můžete změnit dvěma způsoby:  
  
1. Změnou nastavení <xref:System.Threading.ExecutionContext> pro potlačení toku na základě jednotlivých vláken (viz metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>).  
  
2. Změnou výchozího režimu procesu na režim kompatibility verze 1, kde objekt <xref:System.Security.Principal.WindowsIdentity> neprovádí tok napříč žádným asynchronním bodem bez ohledu na nastavení <xref:System.Threading.ExecutionContext> v aktuálním vlákně. Způsob změny výchozího režimu závisí na tom, zda používáte spravovaný spustitelný soubor nebo nespravované rozhraní hostování pro načtení modulu CLR:  
  
    1. U spravovaných spustitelných souborů je nutné nastavit atribut `enabled` elementu [\<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true`.  
  
    2. U nespravovaných hostitelských rozhraní nastavte příznak `STARTUP_LEGACY_IMPERSONATION` v parametru `startupFlags` při volání funkce `CorBindToRuntimeEx`.  
  
     Režim kompatibility verze 1 se vztahuje na celý proces a na všechny domény aplikace v procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
