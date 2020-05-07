---
title: ICorDebugCode3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 6f66e4a903be2e9b12a573f74638a62c58005689
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893458"
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 – rozhraní
Poskytuje metodu, která rozšiřuje "ICorDebugCode" a "ICorDebugCode2", aby poskytovala informace o spravované návratové hodnotě.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReturnValueLiveOffset – metoda](icordebugcode3-getreturnvalueliveoffset-method.md)|U zadaného posunu IL Získá nativní posuny, kde by měla být umístěna zarážka, aby ladicí program mohl získat návratovou hodnotu z funkce.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugILFrame3 – rozhraní](icordebugilframe3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
