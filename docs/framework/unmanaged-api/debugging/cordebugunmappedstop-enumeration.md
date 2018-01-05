---
title: "CorDebugUnmappedStop – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUnmappedStop
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUnmappedStop
helpviewer_keywords: CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5700a9a058a349ea70020bafb7d4bed73d1f53f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop – výčet
Určuje typ nenamapovaný kód, který můžete aktivovat zastavení provádění kódu pomocí krokovače.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`STOP_NONE`|Není zastavit v libovolný typ nenamapovaný kódu.|  
|`STOP_PROLOG`|Zastavte v kódu prologu.|  
|`STOP_EPILOG`|Zastavte v epilogu kódu.|  
|`STOP_NO_MAPPING_INFO`|Zastavte v kódu, který neobsahuje žádné informace o mapování.|  
|`STOP_OTHER_UNMAPPED`|Zastavte v nenamapovaný kód, který se nevejde do prologu epilogu, ne informace mapování nebo nespravované kategorie.|  
|`STOP_UNMANAGED`|Zastavte v nespravovaném kódu. Tato hodnota je platný pouze s spolupráce ladění.|  
|`STOP_ALL`|Zastavte všechny typy nenamapovaný kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Použití [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metodu a nastavit příznaky, které zadejte kód nenamapovaný, ve kterém krokovač zastaví.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
