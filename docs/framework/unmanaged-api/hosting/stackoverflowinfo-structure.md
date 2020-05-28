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
ms.openlocfilehash: 941093b9a0856c2b716ba359c854473f3c9ea26a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006516"
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
  
|Člen|Description|  
|------------|-----------------|  
|`soType`|Hodnota výčtu [StackOverflowType –](stackoverflowtype-enumeration.md) , která určuje typ přetečení.|  
|`pExceptionInfo`|Ukazatel na `EXCEPTION_POINTERS` objekt Win32, který obsahuje záznam výjimky s popisem výjimky a záznamem kontextu s popisem procesoru závislého na počítači v době výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 `StackOverflowInfo`Objekt je předán metodě [IActionOnCLREvent –::](iactiononclrevent-onevent-method.md) prohledatelné `Event_StackOverflow` události.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro hostování](hosting-structures.md)
