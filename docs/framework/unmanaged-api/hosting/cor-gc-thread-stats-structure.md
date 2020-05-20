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
ms.openlocfilehash: 88e81779fc9c20c506f3b0aa11ac2da3958dfe86
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616694"
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
|`PerThreadAllocation`|Počet bajtů paměti přidělených vláknu, které je přidruženo k aktuální `COR_GC_THREAD_STATS` instanci. U tohoto čísla se vymaže nula pokaždé, když dojde k uvolnění paměti bez generace.|  
|`Flags`|Počet bajtů povýšených na vyšší generaci při nejnovějším uvolňování paměti.|  
  
## <a name="remarks"></a>Poznámky  
 [ICLRTask:: getmemstats –](iclrtask-getmemstats-method.md) přebírá výstupní parametr typu `COR_GC_THREAD_STATS` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro hostování](hosting-structures.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
