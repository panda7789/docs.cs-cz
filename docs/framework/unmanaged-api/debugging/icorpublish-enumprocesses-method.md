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
ms.openlocfilehash: eb4096b0ae083e0b6c0598ea18cc8b33c2fdfe3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116292"
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
  
## <a name="parameters"></a>Parametry  
 `Type`  
 Hodnota [cor_pub_enumprocess –](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) výčet, který určuje typ procesu, který se má načíst. V aktuální verzi je platný pouze COR_PUB_MANAGEDONLY.  
  
 `ppIEnum`  
 Ukazatel na adresu [icorpublishprocessenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instanci, která je enumerátor procesy.  
  
## <a name="remarks"></a>Poznámky  
 Čítače výčtu kolekce procesů je založena na snímek procesy, které jsou spuštěny při `EnumProcesses` metoda je volána. Enumerátor nebude obsahovat žádné procesy, které ukončí před nebo po spuštění `EnumProcesses` je volána.  
  
 `EnumProcesses` Metoda může být volána více než jednou v tomto [icorpublish –](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance má vytvořit novou kolekci aktuálních procesů. Stávajících kolekcí nebudou vztahovat následných volání `EnumProcesses` metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorPublish – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
