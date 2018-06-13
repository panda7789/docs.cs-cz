---
title: IGCHost::GetThreadStats – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74827fac102ee6045965f4ba9d74dd3b1aa0af86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437567"
---
# <a name="igchostgetthreadstats-method"></a>IGCHost::GetThreadStats – metoda
Získá statistiku objektů vlákno pro uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFiberCookie`  
 [v] Ukazatel na fiber souboru cookie, který určuje vlákno, pro které chcete získat statistiku.  
  
 `pStats`  
 [ve out] Ukazatel [cor_gc_thread_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) struktura, která obsahuje statistiku kolekce uvolňování paměti pro zadanou vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl, GCHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
