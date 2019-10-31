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
ms.openlocfilehash: c86786a34ff236fb57a1ea6bc4d00b9cd5c4a717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134886"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats – metoda
Získá statistiku pro aktuální stav systému uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStats`  
 [in, out] Ukazatel na strukturu [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) , která obsahuje statistiku pro aktuální stav systému uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 Statistiku může používat systém inteligentního přidělování dat, aby mohl systém uvolňování paměti pracovat. Systém přidělení může například určit, že po kontrole statistiky bude nutné přidat více paměti nebo vynutit kolekci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl, GCHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
