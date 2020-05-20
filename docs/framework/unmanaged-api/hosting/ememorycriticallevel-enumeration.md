---
title: EMemoryCriticalLevel – výčet
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 248f1d281697923e2da14517ca174fe615bba4ff
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616200"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel – výčet
Obsahuje hodnoty, které indikují dopad selhání při požadavku na přidělení konkrétní paměti, ale nelze je splnit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eAppDomainCritical`|Označuje, že přidělení je kritické pro spouštění spravovaného kódu v doméně, která požadovala přidělení. Pokud nelze přidělit paměť, CLR nemůže zaručit, že je doména stále použitelná. Hostitel rozhodne, jakou akci provést v případě, že přidělení nelze splnit. Může vyžádat, aby CLR přerušuje `AppDomain` automaticky, nebo aby mohl být spuštěn voláním metod v [ICLRPolicyManager](iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Označuje, že přidělení je kritické pro spuštění spravovaného kódu v procesu. Tato hodnota se používá při spuštění a při spuštění finalizační metody. Pokud nelze přidělit paměť, modul CLR nemůže v procesu pracovat. Pokud se přidělení nepovede, CLR je efektivně zakázaný. Všechna následující volání do CLR selžou s HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Indikuje, že přidělení je důležité pro spuštění úlohy, která požadovala přidělení. Pokud nelze přidělit paměť, CLR nemůže zaručit, že úlohu lze provést. V případě selhání vyvolá CLR ve <xref:System.Threading.ThreadAbortException> vlákně fyzického operačního systému.|  
  
## <a name="remarks"></a>Poznámky  
 Metody přidělování paměti definované v rozhraních [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) a [IHostMalloc](ihostmalloc-interface.md) přebírají parametr tohoto typu. V závislosti na závažnosti selhání se hostitel může rozhodnout, jestli má požadavek na přidělení selhat okamžitě, nebo počkat, až bude možné ho splnit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRMemoryNotificationCallback – rozhraní](iclrmemorynotificationcallback-interface.md)
- [Výčty hostování](hosting-enumerations.md)
