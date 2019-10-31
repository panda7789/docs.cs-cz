---
title: IGCHost::SetGCStartupLimits – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 1ae50fb3ff15097f9a6ca5839f3832bcfc58d3f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134858"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits – metoda
Nastaví velikost segmentu a maximální velikost pro generaci 0.  
  
> [!IMPORTANT]
> Počínaje .NET Framework 4,5 můžete nastavit velikost segmentu a maximální velikost generace 0 na hodnoty větší než `DWORD` pomocí metody [IGCHost2 –:: SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `SegmentSize`  
 pro Velikost segmentu používaného systémem uvolňování paměti.  
  
 `MaxGen0Size`  
 pro Maximální velikost pro generaci 0  
  
## <a name="remarks"></a>Poznámky  
 Metodu `SetGCStartupLimits` lze volat pouze jednou. Tyto hodnoty nelze později změnit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl, GCHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
