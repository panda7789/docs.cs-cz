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
ms.openlocfilehash: 24a386fe82bbd004954924a573c090af7f58824a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
|`PerThreadAllocation`|Počet bajtů paměti přidělené na vlákno, které souvisí s aktuálním `COR_GC_THREAD_STATS` instance. Toto číslo je zrušeno na nulu pokaždé, když dojde k nule generování uvolnění paměti.|  
|`Flags`|Počet bajtů povýšen na vyšší generace uvolňování paměti na poslední.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrtask::getmemstats –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) trvá výstupní parametr typu `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
