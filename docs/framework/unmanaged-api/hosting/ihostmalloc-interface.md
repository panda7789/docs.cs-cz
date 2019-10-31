---
title: IHostMalloc – rozhraní
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136781"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vyžadovat jemně odstupňované přidělení z haldy prostřednictvím hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy.|  
|[DebugAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy a dále sledoval, kde byla paměť přidělena.|  
|[Free – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Uvolní paměť, která byla přidělena pomocí metody `Alloc`.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR získá ukazatel rozhraní na instanci `IHostMalloc` voláním metody [IHostMemoryManager:: CreateMalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
