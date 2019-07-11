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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 593644802fa490c80b361bfdad3473abe4e82922
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740275"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>Výčet CorDebugCodeInvokePurpose
Popisuje, proč exportované funkce volá spravovaný kód.  
  
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
|`CODE_INVOKE_PURPOSE_NONE`|Žádné nebo neznámý.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Spravovaný kód se spustí všechny spravovaný vstupní bod, jako je například reverzní p-invoke. Jakýkoli účel podrobnější neznámý modul runtime.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Spravovaný kód se spustí statický konstruktor.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Spravovaný kód se spustí provádění pro některé metody rozhraní, která byla volána.|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je používán [icordebugprocess6::getexportstepinfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodu k dispozici informace o procházení spravovaného kódu.  
  
> [!NOTE]
>  Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
