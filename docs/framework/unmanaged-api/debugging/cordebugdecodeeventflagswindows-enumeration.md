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
ms.openlocfilehash: fa8bbcf4d8e5aadee6a4250d23842187d6c2af09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
|`IS_FIRST_CHANCE`|Označuje, že událost ladění je první odpovídající výjimce.|  
  
## <a name="remarks"></a>Poznámky  
 [Icordebugprocess6::decodeevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda zahrnuje `dwFlags` parametr, který obsahuje další informace o ladění událostí a jehož hodnota je závislá na cílové architektury. `CorDebugDecodeEventFlagsWindows` Výčtu lze použít s událostmi ladění na platformě Windows.  
  
> [!NOTE]
>  Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
