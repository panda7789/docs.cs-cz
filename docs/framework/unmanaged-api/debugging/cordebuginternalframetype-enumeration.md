---
title: "CorDebugInternalFrameType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInternalFrameType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugInternalFrameType
helpviewer_keywords: CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b21e50c86a09092e7df65e5fddefb515f6838b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType – výčet
Určuje typ rámce zásobníku. Tento výčet je používán [icordebuginternalframe::getframetype –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`STUBFRAME_NONE`|Hodnotu null. `ICorDebugInternalFrame::GetFrameType` Metoda nikdy vrátí tuto hodnotu.|  
|`STUBFRAME_M2U`|Spravované na nespravované se zakázaným inzerováním rámce.|  
|`STUBFRAME_U2M`|Rámce nespravovaného do spravovaného kódu.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Přechod mezi doménami aplikací.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Volání metody lightweight.|  
|`STUBFRAME_FUNC_EVAL`|Spuštění funkce vyhodnocování.|  
|`STUBFRAME_INTERNALCALL`|Interní volání do modulu CLR.|  
|`STUBFRAME_CLASS_INIT`|Spuštění inicializaci třídy.|  
|`STUBFRAME_EXCEPTION`|Výjimka, která je vyvolána výjimka.|  
|`STUBFRAME_SECURITY`|Rámce, který se používá pro zabezpečení přístupu kódu.|  
|`STUBFRAME_JIT_COMPILATION`|Modul runtime je JIT – kompilace metodu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
