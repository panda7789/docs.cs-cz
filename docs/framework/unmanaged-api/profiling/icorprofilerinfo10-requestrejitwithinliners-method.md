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
ms.openlocfilehash: 00bfc9fc21ed39226fd21c4096305c254d73ee11
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665717"
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

#### <a name="parameters"></a>Parametry

`dwRejitFlags` \
pro Bitová maska [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).

`cFunctions` \
pro Počet funkcí, které mají být rekompilovány.

`moduleIds` \
pro Určuje část párů (`module`, `methodDef`), které identifikují funkce, které mají být znovu zkompilovány. `moduleId`

`methodIds` \
pro Určuje část párů (`module`, `methodDef`), které identifikují funkce, které mají být znovu zkompilovány. `methodId`

## <a name="remarks"></a>Poznámky

[RequestReJIT –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) neprovádí žádné sledování s vloženými metodami. Bylo očekáváno, že Profiler buď zablokuje vkládání, nebo sleduje vkládání `RequestReJIT` a volání všech zapsaných informací, aby bylo zajištěno, že všechny instance ReJITted metody byly vyvolány. To představuje problém s ReJIT při připojení, protože Profiler není k dispozici pro monitorování vkládání. Tuto metodu lze volat, aby bylo zaručeno, že celá sada linií ReJITted bude také.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Hlaviček** CorProf.idl, CorProf.h

**Knihovna** CorGuids.lib

**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
