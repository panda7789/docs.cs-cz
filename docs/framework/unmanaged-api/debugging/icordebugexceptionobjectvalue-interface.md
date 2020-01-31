---
title: ICorDebugExceptionObjectValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: fa154d0bb48f4ecd4fc6a50ce22fd13c592b7c40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782737"
---
# <a name="icordebugexceptionobjectvalue-interface"></a>ICorDebugExceptionObjectValue – rozhraní
Rozšiřuje rozhraní "ICorDebugObjectValue", aby poskytovala informace o trasování zásobníku z objektu spravované výjimky.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateExceptionCallStack – metoda](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|Načte enumerátor do zásobníku volání vložený v objektu výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 Volání `QueryInterface` bude úspěšné pro spravované objekty, které jsou odvozeny z <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
