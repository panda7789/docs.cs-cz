---
title: METAHOST_POLICY_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
ms.openlocfilehash: bb40ed65a2e34f1bf293e4c4c842d7db63d2eaa5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008440"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS – výčet
Poskytuje zásady vytváření vazeb, které jsou společné pro většinu hostitelů modulu runtime. Tento výčet používá metoda [ICLRMetaHostPolicy –:: GetRequestedRuntime –](iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Definuje zásadu s vysokou kompatibilitou, která nebere v úvahu žádný modul CLR (Common Language Runtime), který je načten do aktuálního procesu. Místo toho zvažuje pouze nainstalované CLRs a předvolby komponenty, jak je odvozeno od samotného souboru sestavení, deklarované předdefinované verze nebo konfiguračního souboru.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Aplikuje zásadu upgradu na výsledek vázání verze, když se nenalezne přesná shoda na základě obsahu HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\Policy\Upgrades. To má stejný účinek jako [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Výsledky vazby jsou vráceny, jako kdyby byla v novém procesu spuštěna image poskytnutá voláním. V současné době `GetRequestedRuntime` ignoruje sadu běhových prostředí spustitelný a váže se k sadě instalovaných modulů runtime. Tento příznak umožňuje hostiteli určit, ke kterému modulu runtime se připojí EXE při jeho spuštění.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Pokud `GetRequestedRuntime` není možné najít modul runtime, který je kompatibilní se vstupními parametry, zobrazí se dialogové okno s chybou. Počínaje .NET Framework 4,5 může toto dialogové okno s chybou mít podobu dialogového okna funkce systému Windows, které se zeptá, jestli chce uživatel povolit příslušnou funkci.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`používá bitovou kopii procesu (a odpovídající konfigurační soubor) jako další vstup k procesu vazby. Ve výchozím nastavení se nevrátí `GetRequestedRuntime` k cestě k bitové kopii procesu (obvykle se jedná o soubor exe, který se použil ke spuštění procesu) při určení modulu runtime, ke kterému se má vytvořit vazba.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`je nutné ověřit, zda je příslušná SKU nainstalována, když v konfiguračním souboru nejsou k dispozici žádné informace. To umožňuje aplikacím, které nemají konfigurační soubory, řádně selhat na menších SKU, než je výchozí instalace .NET Framework. Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, zda je příslušná SKU nainstalována, pokud není zadán atribut SKU v elementu konfiguračního souboru `<supportedRuntime />` .|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`má ignorovat SEM_FAILCRITICALERRORS (což je nastaveno voláním funkce [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) ) a zobrazí dialogové okno chyby. Ve výchozím nastavení SEM_FAILCRITICALERRORS potlačuje dialogové okno chyby. Mohla být zděděná z jiného procesu a tichá chyba může být ve vašem scénáři nežádoucí.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Metahost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
- [GetRequestedRuntime – metoda](iclrmetahostpolicy-getrequestedruntime-method.md)
