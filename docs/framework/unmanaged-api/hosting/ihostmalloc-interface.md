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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbf889aaa6a78e67d0f08758adc0bf31cd932e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmalloc-interface"></a>IHostMalloc – rozhraní
Poskytuje metody, které povolit modul CLR (CLR) do požádat podrobných přidělení haldy prostřednictvím hostitele.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Požadavky, že hostitel přidělit požadované množství paměti z haldě.|  
|[DebugAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Požadavky, přidělit požadované množství paměti z haldy hostitel a dále sledovat, kdy byl přidělen paměť.|  
|[Free – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Uvolní paměť, která byla přidělena pomocí `Alloc` metoda.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR získá ukazatele rozhraní k `IHostMalloc` instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
