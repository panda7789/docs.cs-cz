---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: df9ecc9bc355c12f993763820eb5065ba8bcc36b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855914"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3 – metoda

Mapuje ukazatel na instrukci spravovaného kódu na FunctionID. Tato metoda spolupracuje s dynamickými i nedynamickými metodami.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

#### <a name="parameters"></a>Parametry

`ip` \
pro Ukazatel na instrukci ve spravovaném kódu.

`pFunctionId` \
mimo ID funkce

`pReJitId` \
mimo Identita funkce Rekompilované verze JIT.

## <a name="remarks"></a>Poznámky

Tato metoda spolupracuje s dynamickými i nedynamickými metodami. Je nadmnožinou [getfunctionfromip2 –](icorprofilerinfo4-getfunctionfromip2-method.md), která funguje pouze pro funkce s metadaty.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlaviček** CorProf.idl, CorProf.h

**Knihovna** CorGuids.lib

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
