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
ms.openlocfilehash: 7e1965917e8a1c5ae07cf119df3664b969a979be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969255"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost – funkce
Umožňuje hostitelům načíst zadanou verzi modulu CLR (Common Language Runtime) do procesu.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
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
 pro Řetězec, který popisuje verzi CLR, kterou chcete načíst.  
  
 Číslo verze v .NET Framework se skládá ze čtyř částí oddělených tečkami: *hlavní_verze. podverze. sestavení. revize*. Řetězec předaný jako `pwszVersion` musí začínat znakem "v" následovaný prvními třemi částmi čísla verze (například "v 1.0.1529").  
  
 Některé verze modulu CLR jsou nainstalovány s příkazem zásad, který určuje kompatibilitu s předchozími verzemi modulu CLR. Ve výchozím nastavení překrytí po spuštění `pwszVersion` vyhodnocuje příkazy zásad a načte nejnovější verzi modulu runtime, která je kompatibilní s požadovanou verzí. Hostitel může vynutit překrytí a přeskočit vyhodnocení zásad a načíst přesnou verzi určenou `pwszVersion` v předáním hodnoty STARTUP_LOADER_SAFEMODE `startupFlags` pro parametr.  
  
 Pokud `pwszVersion` je`null,` Metoda nenačte žádnou verzi CLR. Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, což znamená, že se nepodařilo načíst modul runtime.  
  
 `pwszBuildFlavor`  
 pro Řetězec, který určuje, zda má být načten Server nebo pracovní stanice sestavení modulu CLR. Platné hodnoty jsou `svr` a `wks`. Sestavení serveru je optimalizované tak, aby využívalo více procesorů pro uvolňování paměti a aby bylo sestavení pracovní stanice optimalizované pro klientské aplikace běžící na počítači s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načteno sestavení pracovní stanice. Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno i v případě `pwszBuildFlavor` , že je `svr`nastavena na. Pokud `pwszBuildFlavor` je však nastavena na `svr` a souběžné uvolňování paměti zadáno ( `startupFlags` viz popis parametru), je sestavení serveru načteno.  
  
> [!NOTE]
> Souběžné uvolňování paměti není podporováno v aplikacích spouštějících emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64). Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 pro Název konfiguračního souboru hostitele, který určuje verzi modulu CLR, která má být načtena. Pokud název souboru neobsahuje plně kvalifikovanou cestu, předpokládá se, že se soubor nachází ve stejném adresáři jako spustitelný soubor, který provádí volání.  
  
 `pReserved`  
 pro Vyhrazeno pro budoucí rozšíření.  
  
 `startupFlags`  
 pro Sada příznaků, která řídí souběžné uvolňování paměti, doménový kód neutrální a chování `pwszVersion` parametru. Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak. Seznam podporovaných hodnot naleznete v tématu [výčet STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 pro Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) `CLSID` Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 pro `IID` Rozhraní, které požadujete. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 mimo Ukazatel rozhraní na verzi modulu runtime, který byl načten.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** MSCorEE.idl  
  
 **Knihovna** MSCorEE.dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
