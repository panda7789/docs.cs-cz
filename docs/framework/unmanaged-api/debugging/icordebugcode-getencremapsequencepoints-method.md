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
ms.openlocfilehash: 83801f7133df6ffb4bdf4a816142849f40baeb53
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125653"
---
# <a name="icordebugcodegetencremapsequencepoints-method"></a><span data-ttu-id="fe1ed-102">ICorDebugCode::GetEnCRemapSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="fe1ed-102">ICorDebugCode::GetEnCRemapSequencePoints Method</span></span>

<span data-ttu-id="fe1ed-103">Tato metoda není implementována v aktuální verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe1ed-103">This method is not implemented in the current version of the .NET Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe1ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe1ed-104">Syntax</span></span>

```cpp
HRESULT GetEnCRemapSequencePoints(
    [in] ULONG32 cMap,
    [out] ULONG32 *pcMap,
    [out, size_is(cMap), length_is(*pcMap)]
        ULONG32 offsets[]
);
```
