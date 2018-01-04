---
title: "COR_TYPE_LAYOUT – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPE_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPE_LAYOUT
helpviewer_keywords: COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 250d78dd9983b75fa7e1b3cfd99215160fbc2b1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cortypelayout-structure"></a>COR_TYPE_LAYOUT – struktura
Poskytuje informace o rozložení objektu v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`parentID`|Identifikátor nadřazený typ pro tento typ. Toto bude s id typu NULL (token1 = 0, token2 = 0) Pokud id typu odpovídá <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|Základní velikost objektu tohoto typu. Toto je celková velikost pro jiný proměnnou velikostí objekty.|  
|`numFields`|Počet polí součástí objekty tohoto typu.|  
|`boxOffset`|Pokud je tento typ zabalená, počáteční posun objektu polí. Toto pole je platná pouze pro typy hodnot, jako je například primitivních elementů a struktury.|  
|`type`|CorElementType, do které patří tohoto typu.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `numFields` je větší než nula, můžete zavolat [icordebugprocess5::gettypefields –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) metodu za účelem získání informací o pole v tomto typu. Pokud `type` je `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, nebo `ELEMENT_TYPE_SZARRAY`, velikost objekty tohoto typu je proměnná a můžete předat [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) struktury k [icordebugprocess5::getarraylayout – ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
