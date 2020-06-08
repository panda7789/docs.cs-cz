---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495122"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8:: IsFunctionDynamic – metoda

Určuje, jestli funkce nemá přidružená metadata.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a>Parametry

- `functionId`

  \[in] `FunctionID` , který identifikuje příslušnou funkci.

- `isDynamic`

  \[out] ukazatel na `BOOL` , který bude obsahovat hodnotu označující, zda nemá funkce žádná metadata.

## <a name="remarks"></a>Poznámky

Funkce je považována za Dynamic, pokud nemá žádná metadata. Některé metody, jako jsou zástupné procedury IL nebo metody LCG, nemají přidružená metadata, která lze načíst pomocí rozhraní IMetaDataImport API. Tyto metody mohou být v profilerech zjištěny prostřednictvím ukazatelů instrukcí nebo naslouchat [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo8 – rozhraní](icorprofilerinfo8-interface.md)
