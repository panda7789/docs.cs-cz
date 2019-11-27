---
title: ICorProfilerInfo::ForceGC – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 9f97da4e68d4b76178198e91c3fb8f08b56dda7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448183"
---
# <a name="icorprofilerinfoforcegc-method"></a>ICorProfilerInfo::ForceGC – metoda
Vynutí uvolňování paměti v modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ForceGC` musí být volána pouze z vlákna, které nikdy nespouštělo spravovaný kód a nemá v zásobníku žádná zpětná volání profileru. Nejpohodlnější implementace je vytvořit samostatné vlákno v rámci profileru, který při signalizaci zavolá `ForceGC`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
