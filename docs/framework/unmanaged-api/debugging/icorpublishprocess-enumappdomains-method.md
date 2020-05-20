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
ms.openlocfilehash: 0c3b5da52b78150198fa9f910bf01b4657e4eba8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421160"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains – metoda
Získá enumerátor pro domény aplikace v procesu, na který odkazuje tento [ICorPublishProcess](icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 mimo Ukazatel na adresu instance [ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md) , která umožňuje iteraci v kolekci aplikačních domén v tomto procesu.  
  
## <a name="remarks"></a>Poznámky  
 Seznam domén aplikace je založen na snímku domén aplikace, které existují při `EnumAppDomains` volání metody. Tato metoda může být volána více než jednou pro vytvoření nového seznamu v aktuálním stavu. Existující seznamy nebudou ovlivněny následnými voláními této metody.  
  
 Pokud byl proces ukončen, dojde k `EnumAppDomains` chybě s hodnotou HRESULT CORDBG_E_PROCESS_TERMINATED.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl, CorPub. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorPublishProcess – rozhraní](icorpublishprocess-interface.md)
