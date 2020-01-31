---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 5822136eb1a7f582bcfae901a99775950e586198
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863176"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners – metoda

ReJITs požadované metody, jakož i všechny zažádané metody.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>Parametry

- `dwRejitFlags`

  \[in] Bitová maska [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).

- `cFunctions`

  \[v] počet funkcí, které mají být rekompilovány.

- `moduleIds`

  \[in] Určuje `moduleId` část párů (`module`, `methodDef`), které identifikují funkce, které se mají znovu zkompilovat.

- `methodIds`

  \[in] Určuje `methodId` část párů (`module`, `methodDef`), které identifikují funkce, které se mají znovu zkompilovat.

## <a name="remarks"></a>Poznámky

[RequestReJIT –](icorprofilerinfo4-requestrejit-method.md) neprovádí žádné sledování s vloženými metodami. Bylo očekáváno, že Profiler buď zablokuje vkládání, nebo sleduje vkládání a `RequestReJIT` volání pro všechny zaregistrované, aby se zajistilo, že každá instance metody inlineed byla ReJITted. To představuje problém s ReJIT při připojení, protože Profiler není k dispozici pro monitorování vkládání. Tuto metodu lze volat, aby bylo zaručeno, že celá sada linií ReJITted bude také.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo10](icorprofilerinfo10-interface.md)
