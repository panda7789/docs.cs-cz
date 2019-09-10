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
ms.openlocfilehash: 01aa1df27dccf41060083333588e04bc5ea88520
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855926"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8:: IsFunctionDynamic – metoda

Určuje, jestli funkce nemá přidružená metadata.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

#### <a name="parameters"></a>Parametry

`functionId` \
pro  `FunctionID` , Který identifikuje příslušnou funkci.

`isDynamic` \
mimo Ukazatel na `BOOL` , který bude obsahovat hodnotu označující, zda nemá funkce žádná metadata.

## <a name="remarks"></a>Poznámky

Funkce je považována za Dynamic, pokud nemá žádná metadata. Některé metody, jako jsou zástupné procedury IL nebo metody LCG, nemají přidružená metadata, která lze načíst pomocí rozhraní IMetaDataImport API. Tyto metody mohou být v profilerech zjištěny prostřednictvím ukazatelů instrukcí nebo naslouchat [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlaviček** CorProf.idl, CorProf.h

**Knihovna** CorGuids.lib

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
