---
title: CorDebugJITCompilerFlags – výčet
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 8be8ce36b557831bc0997dd1c69abb924390d051
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795817"
---
# <a name="cordebugjitcompilerflags-enumeration"></a>CorDebugJITCompilerFlags – výčet
Obsahuje hodnoty, které mají vliv na chování spravovaného kompilátoru JIT (just-in-time).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|Určuje, že má kompilátor sledovat data kompilace a umožňuje optimalizace.|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|Určuje, že má kompilátor sledovat data kompilace, ale zakáže optimalizace.|  
|`CORDEBUG_JIT_ENABLE_ENC`|Určuje, že má kompilátor sledovat data kompilace, zakázat optimalizace a povolit technologie pro úpravy a pokračování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
