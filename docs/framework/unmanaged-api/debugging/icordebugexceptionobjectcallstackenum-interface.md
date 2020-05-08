---
title: ICorDebugExceptionObjectCallStackEnum::Next – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975989"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum::Next – rozhraní
Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky. Toto rozhraní je podtřídou rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)|Získá zadaný počet objektů [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) , které obsahují informace o zásobníku volání objektu výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugExceptionObjectCallStackEnum` Rozhraní implementuje rozhraní ICorDebugEnum.  
  
 Instance je naplněna objekty [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) voláním metody [ICorDebugExceptionObjectValue –:: EnumerateExceptionCallStack –.](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) `ICorDebugExceptionObjectCallStackEnum` Položky zásobníku volání v kolekci lze vyčíslit voláním metody [ICorDebugExceptionObjectCallStackEnum:: Next.](icordebugexceptionobjectcallstackenum-next-method.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
