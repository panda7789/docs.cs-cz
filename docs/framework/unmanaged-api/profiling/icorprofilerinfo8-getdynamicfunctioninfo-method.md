---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: eaf33f3b0de7a18e400cd16d29c046784e2e190f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495317"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo – metoda

Načte informace o dynamických metodách.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a>Parametry

- `functionId`

  \[in] ID funkce, pro kterou mají být načteny informace.

- `moduleId`

  \[in] ukazatel na modul, ve kterém je definována nadřazená třída funkce.

- `ppvSig`

  \[out] ukazatel na signaturu funkce.

- `pbSig`

  \[out] ukazatel na počet bajtů pro podpis funkce.

- `cchName`

  \[v] maximální velikost `wszName` pole.

- `pcchName`

  \[out] počet znaků v `wszName` poli.

- `wszName`

  \[out] pole `WCHAR` , které je názvem funkce, pokud existuje.

## <a name="remarks"></a>Poznámky

Některé metody, jako jsou zástupné procedury IL nebo LCG, nemají přidružená metadata, která lze načíst pomocí rozhraní API [IMetaDataImport](../metadata/imetadataimport-interface.md) a [IMetaDataImport2](../metadata/imetadataimport2-interface.md) . Tyto metody mohou být v profilerech zjištěny prostřednictvím ukazatelů instrukcí nebo naslouchat [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

Toto rozhraní API je možné použít k načtení informací o dynamických metodách, včetně popisného názvu, pokud je k dispozici.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo8 – rozhraní](icorprofilerinfo8-interface.md)
