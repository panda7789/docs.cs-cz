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
ms.openlocfilehash: c901e21521e941c51939958175a5316808890e9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208613"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue – rozhraní

Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dispose – metoda](icordebughandlevalue-dispose-method.md)|Uvolňuje popisovač, na který odkazuje tento `ICorDebugHandleValue` objekt, bez explicitního uvolnění ukazatele rozhraní.|  
|[GetHandleType – metoda](icordebughandlevalue-gethandletype-method.md)|Získá hodnotu CorDebugHandleType –, která popisuje druh popisovače, na který odkazuje `ICorDebugHandleValue` .|  
  
## <a name="remarks"></a>Poznámky  
 V případě, že došlo k `ICorDebugReferenceValue` narušení objektu při provádění laděného kódu, je zrušeno jeho platnost. `ICorDebugHandleValue`Udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud není explicitně uvolněn.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
