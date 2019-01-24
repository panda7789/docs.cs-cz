---
title: COR_PRF_GC_ROOT_KIND – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd8c5e05d3f331d46b2d31f3f2448a674f090eaf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508615"
---
# <a name="corprfgcrootkind-enumeration"></a>COR_PRF_GC_ROOT_KIND – výčet
Označuje druh kořenové kolekce uvolňování paměti, který je zveřejněný prostřednictvím [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|Kořenový adresář je proměnná v zásobníku.|  
|`COR_PRF_GC_ROOT_FINALIZER`|Kořenový adresář je položka ve frontě finalizační metodu.|  
|`COR_PRF_GC_ROOT_HANDLE`|Kořenový adresář je popisovač kolekce uvolnění paměti.|  
|`COR_PRF_GC_ROOT_OTHER`|Druh root není zadána.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
