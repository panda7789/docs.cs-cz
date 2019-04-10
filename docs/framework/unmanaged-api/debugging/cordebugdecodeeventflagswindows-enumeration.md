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
ms.openlocfilehash: 2d4e006a03db5b16de93dfd07ec7b964db4bfc1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207731"
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

- [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
