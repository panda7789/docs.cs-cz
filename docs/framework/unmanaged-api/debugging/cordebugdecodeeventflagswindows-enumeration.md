---
title: Výčet CorDebugDecodeEventFlagsWindows
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99283200a4e9af2e9232b6ce6c25702f47a5cc42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510205"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a>Výčet CorDebugDecodeEventFlagsWindows
Poskytuje další informace o ladění událostí na platformě Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|Označuje, že událost ladění je výjimka první příležitosti.|  
  
## <a name="remarks"></a>Poznámky  
 [Icordebugprocess6::decodeevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) obsahuje metodu `dwFlags` parametr, který poskytuje další informace o ladění události, a jehož hodnota je závislá na Cílová architektura. `CorDebugDecodeEventFlagsWindows` Výčtu lze použít s výjimky ladění na platformě Windows.  
  
> [!NOTE]
>  Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
