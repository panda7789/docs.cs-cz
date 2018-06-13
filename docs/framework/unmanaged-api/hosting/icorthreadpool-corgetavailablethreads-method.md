---
title: ICorThreadpool::CorGetAvailableThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c4867760807af1bc16f7935923cc2b89c1bfba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436891"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a>ICorThreadpool::CorGetAvailableThreads – metoda
Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorThreadpool – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
