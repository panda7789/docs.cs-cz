---
title: ICorPublish::EnumProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2779138a0999e34ad6424d76ddfebbcfdf611d58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses – metoda
Získá enumerátor pro spravované procesy v tomto počítači spuštěna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`  
 Hodnota [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) výčet, který určuje typ procesu mají být načteny. V aktuální verzi je platný pouze COR_PUB_MANAGEDONLY.  
  
 `ppIEnum`  
 Ukazatel na adresu [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instanci, která je enumerátor procesů.  
  
## <a name="remarks"></a>Poznámky  
 Kolekce je čítač procesů je založena na snímku procesy, které jsou spuštěny při zpracování `EnumProcesses` metoda je volána. Enumerátor nebude obsahovat žádné procesy, které ukončit před nebo po spuštění `EnumProcesses` je volána.  
  
 `EnumProcesses` Metoda může být volána více než jednou v tomto [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instanci můžete vytvořit novou kolekci aktuální procesů. Existující kolekce nebude mít vliv následující volání z `EnumProcesses` metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorPublish – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
