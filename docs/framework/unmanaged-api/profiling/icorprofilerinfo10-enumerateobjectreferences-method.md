---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9aadf9701444d215291b6fc19cc8cd61ca832837
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452237"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10:: EnumerateObjectReferences – metoda

Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a>Parametry

- `objectId`

  \[v] objekt pro zobrazení výčtu odkazů.

- `callback`

  \[v] funkce, která bude volána s odkazy pro objekt.

- `clientData`

  \[v] data poskytnutá profilerem, která se mají předat funkci `callback`.

## <a name="remarks"></a>Poznámky

Metoda `EnumerateObjectReferences` je podobná [objectReferences –](icorprofilercallback-objectreferences-method.md), s tím rozdílem, že prochází odkazy na vyžádání pro Profiler místo předběžného přidělení pole pro uložení odkazů.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Viz také

- [Rozhraní ICorProfilerInfo10](icorprofilerinfo10-interface.md)
