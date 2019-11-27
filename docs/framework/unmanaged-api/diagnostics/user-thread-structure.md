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
ms.openlocfilehash: 51db7a2b6464b562e09ce061991898a8d604ead1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437965"
---
# <a name="user_thread-structure"></a>USER_THREAD – struktura
Poskytuje informace ladicímu programu o vlákně. Další informace naleznete v tématu metoda [INotifySource2 –:: setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) .  
  
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
  
## <a name="see-also"></a>Viz také:

- [SetNotifyFilter – metoda](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
