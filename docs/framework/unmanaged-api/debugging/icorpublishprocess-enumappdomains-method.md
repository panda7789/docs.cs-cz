---
title: ICorPublishProcess::EnumAppDomains – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c938adb518fe8c2bd7ac59fe47d7cd2a4f6df886
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492761"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains – metoda
Získá enumerátor pro domény aplikace v procesu, který se odkazuje v tomto [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Ukazatel na adresu [icorpublishappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instanci, která umožňuje iteraci prostřednictvím kolekce aplikační domény v tomto procesu.  
  
## <a name="remarks"></a>Poznámky  
 Seznam domén aplikace je založena na snímek domény aplikace, které existují při `EnumAppDomains` metoda je volána. Tato metoda může být volána více než jednou. Chcete-li vytvořit nový seznam aktuální. Existující seznamy tyto zásady neovlivní z následných volání této metody.  
  
 Pokud proces byl ukončen, `EnumAppDomains` dojde k selhání s hodnotou HRESULT CORDBG_E_PROCESS_TERMINATED.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorPublishProcess – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
