---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 49de3383902791b1278e7c9221a80c3454eb12a2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868917"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a>ICorProfilerInfo10:: ResumeRuntime – metoda

Obnoví modul runtime bez provedení GC.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo10](icorprofilerinfo10-interface.md)
