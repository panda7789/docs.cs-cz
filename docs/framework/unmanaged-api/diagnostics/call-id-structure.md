---
title: "CALL_ID – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71fd69cbcced1440839b9eedf8fbe3d8f5b90646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="callid-structure"></a>CALL_ID – struktura
Poskytuje informace o funkci, která je volána ladicí program. Najdete v článku [inotifysink2 –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) rozhraní pro další informace.  
  
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
|`szMachine`|Identifikuje počítač, který je uskutečněním hovoru.|  
|`dwPid`|Identifikuje počítač procesoru.|  
|`pUserThread`|Identifikuje vlákno, které provádí volání.|  
|`addrStackPointer`|Určuje adresu zásobníku volání.|  
|`szEntryPoint`|Určuje adresu volání.|  
|`szDestinationMachine`|Identifikuje počítač, který provede volání.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také  
 [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
