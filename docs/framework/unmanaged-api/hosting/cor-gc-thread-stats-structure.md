---
title: COR_GC_THREAD_STATS – struktura
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a4b56270318a05d0e5a480fdb56eb45593d5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177733"
---
# <a name="corgcthreadstats-structure"></a>COR_GC_THREAD_STATS – struktura
Obsahuje vlákno statistiky týkající se uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`PerThreadAllocation`|Počet bajtů paměti přidělené ve vlákně, které souvisí s aktuálním `COR_GC_THREAD_STATS` instance. Toto číslo se vymaže na nulu pokaždé, když dojde k uvolnění paměti generace nula.|  
|`Flags`|Počet bajtů povýšen na vyšší generaci uvolňování paměti na poslední.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrtask::getmemstats –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) trvá výstupní parametr typu `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
