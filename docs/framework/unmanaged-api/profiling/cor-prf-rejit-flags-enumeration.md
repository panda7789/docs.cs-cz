---
title: COR_PRF_REJIT_FLAGS – výčet
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177103"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>COR_PRF_REJIT_FLAGS – výčet
Obsahuje hodnoty, které označují, jak by se mělo chovat rozhraní API [ICorProfilerInfo10::RequestReJITWithInliners.](icorprofilerinfo10-requestrejitwithinliners-method.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| ReJITted metody budou blokovány v zařadit do jiných metod. |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| Příjem `GetFunctionParameters` zpětná volání pro všechny metody, které vinárně metody požadované reJITted. |  

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [operační systémy podporované rozhraním .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]
  
## <a name="see-also"></a>Viz také

- [Výčty pro profilaci](profiling-enumerations.md)
