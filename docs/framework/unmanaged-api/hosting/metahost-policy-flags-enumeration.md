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
ms.openlocfilehash: f980fb1336adaf43091e41b9e42ea008b00c033f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447275"
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS – výčet
Poskytuje vazby zásady, které jsou společné pro většinu modulu runtime. Tento výčet je používán [iclrmetahostpolicy::getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda.  
  
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
|`METAHOST_POLICY_HIGHCOMPAT`|Definuje zásady vysokou kompatibility, které nebere v úvahu žádné modul common language runtime (CLR), který je načten do aktuální proces. Místo toho považuje pouze nainstalované CLRs a předvolby součásti, odvozené z samotný soubor sestavení, verze deklarované vytvořené proti nebo konfiguračního souboru.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Pro výsledek vazby verze platí zásady upgradu, pokud není nalezena přesná shoda na základě obsahu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Tato akce nemá stejný účinek jako [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Vazba výsledky se vrátí, jako kdyby bitovou kopii zadaná pro volání nebyly spuštěny v nový proces. V současné době `GetRequestedRuntime` ignoruje sadu načíst moduly runtime a sváže s sadu nainstalované moduly runtime. Tento příznak umožňuje hostitelům určit, které runtime EXE vytvoří vazbu k při jeho spuštění.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Zobrazí se dialogové okno chyby, pokud `GetRequestedRuntime` se nepodařilo najít modul runtime, který je kompatibilní s vstupní parametry. Od verze [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], toto dialogové okno chyby můžete mít formu funkce Windows dialogové okno s dotazem, zda uživatel chcete povolit příslušné funkce.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` používá jako další vstup pro proces vytváření vazby bitovou kopii procesu (a všechny odpovídající soubor konfigurace). Ve výchozím nastavení `GetRequestedRuntime` nepřecházely k cesta bitové kopie proces (obvykle EXE, který byl použitý ke spuštění procesu) při určování modulu runtime pro vazbu.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` musí zkontrolovat, zda je nainstalována příslušné SKU, pokud v konfiguračním souboru nejsou dostupné žádné informace. To umožňuje aplikacím, které nemají konfigurační soubory řádně selhání na menší SKU než výchozí instalace rozhraní .NET Framework. Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající verze SKU, pokud atribut SKU je uveden v konfiguračním souboru `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` musí zkontrolovat, zda je nainstalována příslušné SKU, pokud v konfiguračním souboru nejsou dostupné žádné informace. To umožňuje aplikacím, které nemají konfigurační soubory řádně selhání na menší SKU než výchozí instalace rozhraní .NET Framework. Ve výchozím nastavení `GetRequestedRuntime` nekontroluje, jestli je nainstalovaná odpovídající verze SKU, pokud atribut SKU je uveden v konfiguračním souboru `<supportedRuntime />` elementu.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` třeba ignorovat SEM_FAILCRITICALERRORS (který je nastaven při volání [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkce) a zobrazit dialogové okno chyby. Ve výchozím nastavení potlačí SEM_FAILCRITICALERRORS dialogové okno chyby. Ho může mít bylo zděděno z jiného procesu a tichou chyba může být žádoucí ve vašem scénáři.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Metahost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
