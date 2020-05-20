---
title: USER_THREAD – struktura
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609440"
---
# <a name="user_thread-structure"></a>USER_THREAD – struktura
Poskytuje informace ladicímu programu o vlákně. Další informace naleznete v tématu metoda [INotifySource2 –:: setnotifyfilter –](inotifysource2-setnotifyfilter-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`pSidBuffer`|Adresa vyrovnávací paměti vlákna.|  
|`dwSidLen`|Délka vyrovnávací paměti vlákna (v bajtech).|  
|`dwTid`|ID vlákna.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také

- [SetNotifyFilter – metoda](inotifysource2-setnotifyfilter-method.md)
- [Struktury úložiště symbolů diagnostiky](diagnostics-symbol-store-structures.md)
