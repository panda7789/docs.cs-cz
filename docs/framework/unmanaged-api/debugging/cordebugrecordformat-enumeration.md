---
title: "Výčet CorDebugRecordFormat"
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
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eaf962250d97f031eaa60b7cc0b15622897aad3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugrecordformat-enumeration"></a>Výčet CorDebugRecordFormat
Popisuje formát dat v bajtové pole obsahující informace o události ladění nativního výjimka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|Data je záznam 32bitová verze Windows výjimky.|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|Data je záznam 64bitová verze Windows výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 Členem `CorDebugRecordFormat` předaný výčet [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda udávajících formát bajtového pole v jeho `pRecord` argument.  
  
> [!NOTE]
>  Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
