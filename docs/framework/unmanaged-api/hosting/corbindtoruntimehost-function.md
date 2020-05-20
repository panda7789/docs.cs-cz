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
ms.openlocfilehash: afb25ad9e1760f390aa8dfb3e1de39ea60f185c2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616616"
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
  
 Některé verze modulu CLR jsou nainstalovány s příkazem zásad, který určuje kompatibilitu s předchozími verzemi modulu CLR. Ve výchozím nastavení překrytí po spuštění vyhodnocuje `pwszVersion` příkazy zásad a načte nejnovější verzi modulu runtime, která je kompatibilní s požadovanou verzí. Hostitel může vynutit překrytí a přeskočit vyhodnocení zásad a načíst přesnou verzi určenou v `pwszVersion` předáním hodnoty STARTUP_LOADER_SAFEMODE pro `startupFlags` parametr.  
  
 Pokud `pwszVersion` je `null,` Metoda nenačte žádnou verzi CLR. Místo toho vrátí CLR_E_SHIM_RUNTIMELOAD, což znamená, že se nepodařilo načíst modul runtime.  
  
 `pwszBuildFlavor`  
 pro Řetězec, který určuje, zda má být načten Server nebo pracovní stanice sestavení modulu CLR. Platné hodnoty jsou `svr` a `wks` . Sestavení serveru je optimalizované tak, aby využívalo více procesorů pro uvolňování paměti a aby bylo sestavení pracovní stanice optimalizované pro klientské aplikace běžící na počítači s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načteno sestavení pracovní stanice. Při spuštění v počítači s jedním procesorem je sestavení pracovní stanice vždy načteno i v případě, že `pwszBuildFlavor` je nastavena na `svr` . Pokud je však `pwszBuildFlavor` nastavena na `svr` a souběžné uvolňování paměti zadáno (viz popis `startupFlags` parametru), je sestavení serveru načteno.  
  
> [!NOTE]
> Souběžné uvolňování paměti není podporováno v aplikacích spouštějících emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64). Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 pro Název konfiguračního souboru hostitele, který určuje verzi modulu CLR, která má být načtena. Pokud název souboru neobsahuje plně kvalifikovanou cestu, předpokládá se, že se soubor nachází ve stejném adresáři jako spustitelný soubor, který provádí volání.  
  
 `pReserved`  
 pro Vyhrazeno pro budoucí rozšíření.  
  
 `startupFlags`  
 pro Sada příznaků, která řídí souběžné uvolňování paměti, doménový kód neutrální a chování `pwszVersion` parametru. Výchozí hodnota je jedna doména, pokud není nastaven žádný příznak. Seznam podporovaných hodnot naleznete v tématu [STARTUP_FLAGS Enumeration](startup-flags-enumeration.md).  
  
 `rclsid`  
 pro `CLSID`Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](iclrruntimehost-interface.md) . Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 pro `IID`Rozhraní, které požadujete. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 mimo Ukazatel rozhraní na verzi modulu runtime, který byl načten.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CorBindToCurrentRuntime – funkce](corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx – funkce](corbindtoruntimeex-function.md)
- [ICorRuntimeHost – rozhraní](icorruntimehost-interface.md)
- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
