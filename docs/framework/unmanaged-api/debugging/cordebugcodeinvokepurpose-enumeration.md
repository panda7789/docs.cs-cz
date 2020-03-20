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
ms.openlocfilehash: f1d4a1e08a63665a532c7aa3572f1e3f9c106ba6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179246"
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
|`CODE_INVOKE_PURPOSE_NONE`|Žádné nebo neznámé.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Spravovaný kód spustí libovolný spravovaný vstupní bod, například reverzní p-invoke. Jakýkoli podrobnější účel není za běhu znám.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Spravovaný kód spustí statický konstruktor.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Spravovaný kód spustí implementaci pro některé metody rozhraní, která byla volána.|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet používá metoda [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o krokování spravovaného kódu.  
  
> [!NOTE]
> Tento výčet je určen pouze pro použití v nativních scénářích ladění .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
