---
title: "CorDebugIlToNativeMappingTypes – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44546c8d66eff111b70673ed63ab82d30fea0b6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a>CorDebugIlToNativeMappingTypes – výčet
Určuje, jestli konkrétní rozsah nativní pokyny, reprezentována instanci cor_debug_il_to_native_map – struktura odpovídá speciální kód oblasti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`NO_MAPPING`|Rozsah nativní pokyny neodpovídá žádné speciální kód oblasti.|  
|`PROLOG`|Rozsah nativní pokyny odpovídá prologu.|  
|`EPILOG`|Rozsah nativní pokyny odpovídá epilogu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
