---
title: CALL_ID – struktura
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 8c606f67766334800444f39b115d90f65ecca13d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448593"
---
# <a name="call_id-structure"></a>CALL_ID – struktura
Poskytuje informace ladicímu programu o funkci, která je volána. Další informace najdete v rozhraní [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`szMachine`|Identifikuje počítač, který provádí volání.|  
|`dwPid`|Identifikuje procesor počítače.|  
|`pUserThread`|Identifikuje vlákno, které provádí volání.|  
|`addrStackPointer`|Určuje adresu zásobníku volání.|  
|`szEntryPoint`|Určuje adresu volání.|  
|`szDestinationMachine`|Identifikuje počítač, který spustí volání.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také:

- [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
