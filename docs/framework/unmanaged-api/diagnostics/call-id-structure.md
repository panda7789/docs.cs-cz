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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6fa729b131d12b2825a2def700fd918ce8acc40
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220172"
---
# <a name="callid-structure"></a>CALL_ID – struktura
Poskytuje informace o ladicím programu o funkci, která je volána. Zobrazit [inotifysink2 –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) rozhraní pro další informace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`dwPid`|Určuje procesor počítače.|  
|`pUserThread`|Identifikuje vlákna, která provádí volání.|  
|`addrStackPointer`|Určuje adresu zásobníku volání.|  
|`szEntryPoint`|Určuje adresu volání.|  
|`szDestinationMachine`|Identifikuje počítač, který provede volání.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také:

- [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
