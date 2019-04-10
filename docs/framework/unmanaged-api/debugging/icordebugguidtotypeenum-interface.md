---
title: ICorDebugGuidToTypeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2ea67c6e4d860d41cfe67aaab73babb51f3ce45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210656"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum – rozhraní
Poskytuje enumerátor, který definuje mapování mezi sadou identifikátorů GUID a jejich odpovídající typy, které jsou znázorněny ICorDebugType instancí. Toto rozhraní dědí z rozhraní ICorDebugEnum metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které se mapují GUID informací o typu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugGuidToTypeEnum` Objektu rozhraní může být načten voláním [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody. Ladicí program může volat toto rozhraní [Další](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodu pro načtení [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekty, které představují mapování ze spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] načíst typy v doména aplikace použít pro volání [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
