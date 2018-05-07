---
title: IGCHost::GetStats – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3e0d6f68ffa5280d4616d4fa4ac60b4cb86f6a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats – metoda
Získá statistiku pro aktuální stav kolekce systém uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStats`  
 [ve out] Ukazatel [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura, která obsahuje statistiku pro aktuální stav kolekce systém uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 Statistiku lze inteligentní přidělení systému pomohou systém kolekce paměti fungovat. Například přidělení systém může určit, po kontrole statistiky, které je nutné přidat více paměti nebo vynutit kolekce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl, GCHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
