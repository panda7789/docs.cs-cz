---
title: ICorDebugArrayValue::GetRank – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
ms.openlocfilehash: e6401731844f2ce7a1d9fec1c94019f763870fe7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894997"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="7d2f3-102">ICorDebugArrayValue::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="7d2f3-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="7d2f3-103">Získá počet rozměrů v poli.</span><span class="sxs-lookup"><span data-stu-id="7d2f3-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d2f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d2f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d2f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d2f3-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="7d2f3-106">mimo Ukazatel na počet dimenzí v tomto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="7d2f3-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d2f3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d2f3-107">Requirements</span></span>  
 <span data-ttu-id="7d2f3-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d2f3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d2f3-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d2f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d2f3-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d2f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d2f3-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d2f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
