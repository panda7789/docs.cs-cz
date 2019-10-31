---
title: StackOverflowInfo – struktura
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: 1072026f92edbc646653c6dd74ec8e22d5b887e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105910"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo – struktura
Ukládá typ přetečení, ke kterému došlo, a informace o výjimce, která byla vyvolána z důvodu přetečení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`soType`|Hodnota výčtu [StackOverflowType –](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) , která určuje typ přetečení.|  
|`pExceptionInfo`|Ukazatel na objekt Win32 `EXCEPTION_POINTERS`, který obsahuje záznam výjimky s popisem výjimky a záznamem kontextu s popisem procesoru závislého na počítači v okamžiku výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 `StackOverflowInfo` objekt je předán metodě [IActionOnCLREvent –::](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) prohledatelné události `Event_StackOverflow`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
