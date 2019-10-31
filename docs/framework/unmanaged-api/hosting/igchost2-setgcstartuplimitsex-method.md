---
title: IGCHost2::SetGCStartupLimitsEx – metoda
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: d78f81093e61c40eaec334f957d8583eeb593f5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134808"
---
# <a name="igchost2setgcstartuplimitsex-method"></a>IGCHost2::SetGCStartupLimitsEx – metoda
Nastaví velikost segmentu a maximální velikost pro generaci 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `SegmentSize`  
 pro Velikost segmentu používaného systémem uvolňování paměti.  
  
 `MaxGen0Size`  
 pro Maximální velikost pro generaci 0  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty, které `SetGCStartupLimitsEx` sady lze zadat pouze před spuštěním hostitele. Tyto hodnoty nelze později změnit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl, GCHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IGCHost2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
