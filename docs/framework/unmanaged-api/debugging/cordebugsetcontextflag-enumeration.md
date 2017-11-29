---
title: "CorDebugSetContextFlag – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugSetContextFlag
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugSetContextFlag
helpviewer_keywords: CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 958ed303fab3dcb01fad2040dd06381e76fe5a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag – výčet
Určuje, zda kontext je z aktivní (nebo listu) s rámečkem v zásobníku nebo je poškozený podle unwinding z jiné rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|SET_CONTEXT_FLAG_ACTIVE_FRAME|Kontext není aktivní kontextu vlákna.|  
|SET_CONTEXT_FLAG_UNWIND_FRAME|Kontext je poškozený podle unwinding z jiné rámce.|  
  
## <a name="remarks"></a>Poznámky  
 `CorDebugSetContextFlag`obsahuje hodnoty, které jsou používány [icordebugstackwalk::setcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
