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
ms.openlocfilehash: 37da471aaa8e9f802a8430d7b3289b375ff1b40a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136986"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS – struktura
Obsahuje statistiku jednotlivých vláken, která souvisí s uvolňováním paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`PerThreadAllocation`|Počet bajtů paměti přidělených vláknu, které je přidruženo k aktuální instanci `COR_GC_THREAD_STATS`. U tohoto čísla se vymaže nula pokaždé, když dojde k uvolnění paměti bez generace.|  
|`Flags`|Počet bajtů povýšených na vyšší generaci při nejnovějším uvolňování paměti.|  
  
## <a name="remarks"></a>Poznámky  
 [ICLRTask:: getmemstats –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) přebírá výstupní parametr typu `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
