---
title: ICorPublishEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d672cf2375a5354c48608b3e4156867ba406992a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765012"
---
# <a name="icorpublishenumclone-method"></a>ICorPublishEnum::Clone – metoda
Vytvoří kopii tohoto [icorpublishenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Ukazatel na adresu `ICorPublishEnum` objekt, který je kopií této `ICorPublishEnum` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorPublishEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
