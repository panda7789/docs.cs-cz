---
title: StackTrace_SimpleContext – struktura
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210422"
---
# <a name="stacktracesimplecontext-structure"></a>StackTrace_SimpleContext – struktura
Poskytuje jednoduchý kontext, který jde použít místo úplné `CONTEXT` struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`StackOffset`|Ukazatel zásobníku a ukazatel zásobníku enter (ESP) na x86 platformy.|  
|`FrameOffset`|Odsazení rámce nebo registru EBP na x86 platformy.|  
|`InstructionOffset`|Ukazatele na instrukci nebo ukazatele na instrukci enter (EIP) na x86 platformy.|  
  
## <a name="remarks"></a>Poznámky  
 Protože funkce trasování zásobníku je obvykle potřeba vrátit pouze adresy, odsazení rámce a adresy zásobníku, můžete volitelně použít `SimpleContext` struktura místo velké `CONTEXT` struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** SOS_Stacktrace.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
