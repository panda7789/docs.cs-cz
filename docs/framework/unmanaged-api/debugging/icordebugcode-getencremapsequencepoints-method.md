---
title: ICorDebugCode::GetEnCRemapSequencePoints – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetEnCRemapSequencePoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetEnCRemapSequencePoints
helpviewer_keywords:
- GetEnCRemapSequencePoints method [.NET Framework debugging]
- ICorDebugCode::GetEnCRemapSequencePoints method [.NET Framework debugging]
ms.assetid: 8463a98a-de4a-418e-beb0-9611885ae6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65218eb6b5ba26bfb1cbee4f1f276c39e8623c5d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700706"
---
# <a name="icordebugcodegetencremapsequencepoints-method"></a>ICorDebugCode::GetEnCRemapSequencePoints – metoda

Tato metoda není implementována v aktuální verzi .NET Framework.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEnCRemapSequencePoints(
    [in] ULONG32 cMap,
    [out] ULONG32 *pcMap,
    [out, size_is(cMap), length_is(*pcMap)]
        ULONG32 offsets[]
);
```
