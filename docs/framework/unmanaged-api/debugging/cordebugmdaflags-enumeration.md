---
title: CorDebugMDAFlags – výčet
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: c7af194351290ad937e40a2fc8b960c2c242629c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132799"
---
# <a name="cordebugmdaflags-enumeration"></a>CorDebugMDAFlags – výčet
Určuje stav vlákna, ve kterém je aktivován pomocník spravovaného ladění (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|Vlákno, ve kterém se aktivovalo MDA, bylo od chvíle, kdy byla vyvolána služba MDA, naproti skluzu.|  
  
## <a name="remarks"></a>Poznámky  
 V případě, že zásobník volání již nepopisuje, kde byl původně vyvolán proces MDA, vlákno jepovažováno za neúspěšně. Jedná se o neobvyklé okolnosti, o jejichž provedení neplatného vlákna po ukončení operace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
