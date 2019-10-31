---
title: Výčet CorDebugCodeInvokePurpose
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: f037a28f0417f5607cd5b5637da4ca62e34e0edb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132268"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>Výčet CorDebugCodeInvokePurpose
Popisuje, proč exportovaná funkce volá spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|Žádná nebo neznámá.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Spravovaný kód spustí všechny spravované vstupní body, jako je reverzní volání nespravovaného kódu. Jakýkoli podrobnější účel není modulem runtime znám.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Spravovaný kód spustí statický konstruktor.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Spravovaný kód spustí implementaci pro některou metodu rozhraní, která byla volána.|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet používá metoda [ICorDebugProcess6:: GetExportStepInfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o prokrokování prostřednictvím spravovaného kódu.  
  
> [!NOTE]
> Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
