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
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804606"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vyžadovat jemně odstupňované přidělení z haldy prostřednictvím hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alloc – metoda](ihostmalloc-alloc-method.md)|Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy.|  
|[DebugAlloc – metoda](ihostmalloc-debugalloc-method.md)|Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy a dále sledoval, kde byla paměť přidělena.|  
|[Free – metoda](ihostmalloc-free-method.md)|Uvolňuje paměť, která byla přidělena pomocí `Alloc` metody.|  
  
## <a name="remarks"></a>Poznámky  
 CLR získá ukazatel rozhraní na `IHostMalloc` instanci voláním metody [IHostMemoryManager:: CreateMalloc –](ihostmemorymanager-createmalloc-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostMemoryManager – rozhraní](ihostmemorymanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
