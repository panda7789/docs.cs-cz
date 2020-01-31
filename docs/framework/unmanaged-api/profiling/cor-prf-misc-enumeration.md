---
title: COR_PRF_MISC – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: fe27c0fca6d38b4cff6cac2b9778cf2be68903a3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867123"
---
# <a name="cor_prf_misc-enumeration"></a>COR_PRF_MISC – výčet
Obsahuje konstantní hodnoty, které určují speciální identifikátory.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|Výchozí identifikátor používaný v [ICorProfilerInfo:: GetModuleInfo –](icorprofilerinfo-getmoduleinfo-method.md) pro modul, který ještě nebyl připojen k sestavení.|  
|`PROFILER_GLOBAL_CLASS`|Výchozí identifikátor třídy pro globální konstanty, které nepatří do třídy.|  
|`PROFILER_GLOBAL_MODULE`|Výchozí identifikátor modulu pro globální objekty, které nepatří do modulu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
