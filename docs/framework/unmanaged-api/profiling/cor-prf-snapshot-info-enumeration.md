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
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867019"
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
  
|Členové|Popis|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback` s výjimkou parametru `context`.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback`, včetně parametru `context`.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Indikuje, že se použije jednodušší algoritmus procházení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty, které jsou poskytovány výčtem `COR_PRF_SNAPSHOT_INFO`, jsou předány jako parametry do metody [DoStackSnapshot –](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [DoStackSnapshot – metoda](icorprofilerinfo2-dostacksnapshot-method.md)
- [Výčty pro profilaci](profiling-enumerations.md)
