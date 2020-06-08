---
title: COR_PRF_SNAPSHOT_INFO – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6168c5b27868a261871b292e17ca02b04ae89917
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500777"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO – výčet
Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce [StackSnapshotCallback –](stacksnapshotcallback-function.md) profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Členové|Description|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Určuje, že hodnoty musí být předány pro všechny `StackSnapshotCallback` parametry s výjimkou `context` parametru.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Určuje, že hodnoty musí být předány pro všechny `StackSnapshotCallback` parametry, včetně `context` parametru.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Indikuje, že se použije jednodušší algoritmus procházení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty, které jsou poskytovány `COR_PRF_SNAPSHOT_INFO` výčtem, jsou předány jako parametry do metody [DoStackSnapshot –](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [DoStackSnapshot – metoda](icorprofilerinfo2-dostacksnapshot-method.md)
- [Výčty pro profilaci](profiling-enumerations.md)
