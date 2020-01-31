---
title: ICorDebugHandleValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794461"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue – rozhraní

Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dispose – metoda](icordebughandlevalue-dispose-method.md)|Uvolňuje popisovač, na který odkazuje tento objekt `ICorDebugHandleValue`, bez explicitního uvolnění ukazatele rozhraní.|  
|[GetHandleType – metoda](icordebughandlevalue-gethandletype-method.md)|Získá hodnotu CorDebugHandleType –, která popisuje druh popisovače, na který odkazuje tento `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt `ICorDebugReferenceValue` je po přerušení v provádění laděného kódu neplatný. `ICorDebugHandleValue` udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud není explicitně uvolněn.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
