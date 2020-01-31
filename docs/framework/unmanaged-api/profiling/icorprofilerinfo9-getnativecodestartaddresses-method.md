---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868275"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses – metoda

S ohledem na functionId a rejitId vytvoří výčet počáteční adresy kódu pro všechny zpracovaných kompilátorem JIT verze tohoto kódu, který aktuálně existuje.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>Parametry

- `functionId`

  \[in] ID funkce, jejíž počáteční adresy nativního kódu by měly být vráceny.

- `reJitId`

  \[in] identita funkce Rekompilované JIT.

- `cCodeStartAddresses`

  \[v] maximální velikost pole `codeStartAddresses`.

- `pcCodeStartAddresses`

  \[] počet dostupných adres.

- `codeStartAddresses`

  \[) pole `UINT_PTR`, z nichž každá z nich představuje počáteční adresu pro nativní tělo zadané funkce.

## <a name="remarks"></a>Poznámky

Pokud je povolená vrstvená kompilace, funkce může mít více než jeden tělo nativního kódu.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo9](icorprofilerinfo9-interface.md)
