---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 95473a8ce8d5fd7540228ecd9767448e51b5b326
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868981"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold – metoda

Získá hodnotu nakonfigurované prahové hodnoty haldy velkého objektu (LOH).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>Parametry

- `pThreshold`

  \[] prahová hodnota haldy pro velké objekty v bajtech.

## <a name="remarks"></a>Poznámky

Objekty větší než prahová hodnota haldy pro velké objekty budou přiděleny na haldu velkých objektů. Počínaje rozhraním .NET Core 3,0 je prahová hodnota haldy velkých objektů konfigurovatelná, `pThreshold` bude obsahovat aktivní mezní velikost haldy velkých objektů v bajtech.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo10](icorprofilerinfo10-interface.md)
