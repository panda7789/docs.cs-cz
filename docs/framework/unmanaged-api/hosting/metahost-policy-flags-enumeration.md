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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a96af0c66d85c7eec9a97be3ba8c756b1e91849
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486672"
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS – výčet
Poskytuje zásady vazby, které jsou společné pro většinu hostitelská prostředí modulu runtime. Tento výčet je používán [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Člen|Popis|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Definuje vysokou kompatibilitu zásady, které nebere v úvahu všechny common language runtime (CLR, který je načten do aktuální proces). Místo toho bude považovat jenom nainstalované CLRs a předvolby komponenty, odvozena z samotný soubor sestavení, verzi deklarované vytvořené před nebo konfiguračního souboru.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Aplikuje zásad upgradu na výsledek vazby verze, když se najde přesná shoda, na základě obsahu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. To má stejný účinek jako [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Vazba výsledky jsou vráceny, jako kdyby byly k dispozici k volání image spustit nový proces. V současné době `GetRequestedRuntime` ignoruje sadu zaveditelný moduly runtime a sváže s sady instalovaných modulů runtime. Tento příznak umožňuje hostiteli zjistit, které modul runtime vytvoří vazbu EXE, když se spustí.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Zobrazí se dialogové okno chyby, pokud `GetRequestedRuntime` se nepodařilo najít modul runtime, který je kompatibilní se vstupními parametry. Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], toto dialogové okno chyby můžete mít formu funkce Windows dialogové okno s dotazem, jestli mu chcete povolit příslušné funkce.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` jako další vstup pro proces vytváření vazby používá image procesu (a všechny odpovídající konfigurační soubor). Ve výchozím nastavení `GetRequestedRuntime` nepřecházel k cestě image proces (obvykle EXE, který byl použit ke spuštění procesu) při určování, modul runtime k vytvoření vazby.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` musíte zkontrolovat, jestli je nainstalovaná odpovídající SKU, když v konfiguračním souboru nejsou dostupné žádné informace. To umožňuje aplikacím, které nemají konfiguračních souborů, aby řádně selhat na SKU nižší než výchozí instalace rozhraní .NET Framework. Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající SKU, pokud je zadán atribut SKU v konfiguračním souboru `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` musíte zkontrolovat, jestli je nainstalovaná odpovídající SKU, když v konfiguračním souboru nejsou dostupné žádné informace. To umožňuje aplikacím, které nemají konfiguračních souborů, aby řádně selhat na SKU nižší než výchozí instalace rozhraní .NET Framework. Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající SKU, pokud je zadán atribut SKU v konfiguračním souboru `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` Ignorovat SEM_FAILCRITICALERRORS (který je nastaven při volání [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkce) a zobrazit dialog s chybou. Ve výchozím nastavení potlačí SEM_FAILCRITICALERRORS dialog s chybou. To může byly zděděny z jiného procesu a tiché chyba může nežádoucí ve vašem scénáři.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Metahost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
