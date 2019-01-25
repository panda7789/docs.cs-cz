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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acc4da79796e975d349d1cb33c301c25c4791cb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709075"
---
# <a name="userthread-structure"></a>USER_THREAD – struktura
Poskytuje informace o vlákno ladicího programu. Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`pSidBuffer`|Adresa vyrovnávací paměti pro vlákno.|  
|`dwSidLen`|Délka vyrovnávací paměti vlákna, v bajtech.|  
|`dwTid`|ID vlákna.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také:
- [SetNotifyFilter – metoda](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
