---
title: "COR_PRF_EX_CLAUSE_INFO – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_EX_CLAUSE_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords: COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9952ea1d8c806c9d3ac5357d933092fb82351484
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corprfexclauseinfo-structure"></a>COR_PRF_EX_CLAUSE_INFO – struktura
Obsahuje informace o instanci klauzule určité výjimky a jeho přidružené rámečku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`clauseType`|Hodnota [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) výčet, který určuje typ výjimky klauzuli právě zadaný kód nebo doleva.|  
|`programCounter`|Nativní vstupní bod obslužné rutiny klauzule – například obsah X86 EIP registru.|  
|`framePointer`|Ukazatel na logické rámce pro obslužnou rutinu klauzule – například obsah X86 EBP registru.|  
|`shadowStackPointer`|Ukazatel zásobníku stínové. Tato hodnota je obsah registru BSP a se vztahuje pouze na IA64.|  
  
## <a name="remarks"></a>Poznámky  
 Po přijetí oznámení o výjimce [ICorProfilerInfo2::getnotifiedexceptionclauseinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) lze použít k získání nativní adresy a rámce informací pro klauzuli výjimky (`catch` / `finally`/filter), má být spuštěna, nebo byla právě spuštěna.  
  
 Provádění klauzule výjimka zahrnuje tyto zpětná volání z common language runtime (CLR):  
  
-   [Icorprofilercallback::exceptioncatcherenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [Icorprofilercallback::exceptionunwindfinallyenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [Icorprofilercallback::exceptionsearchfilterenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [Icorprofilercallback::exceptioncatcherleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [Icorprofilercallback::exceptionunwindfinallyleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [Icorprofilercallback::exceptionsearchfilterleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
