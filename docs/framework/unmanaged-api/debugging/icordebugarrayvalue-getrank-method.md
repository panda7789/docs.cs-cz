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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abf24b81bae4d16c3a03aa668d4e1f5e8117cc93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737459"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="e6b96-102">ICorDebugArrayValue::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="e6b96-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="e6b96-103">Získá počet dimenzí v poli.</span><span class="sxs-lookup"><span data-stu-id="e6b96-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6b96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6b96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6b96-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="e6b96-106">[out] Ukazatel na počet dimenzí v tomto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="e6b96-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b96-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6b96-107">Requirements</span></span>  
 <span data-ttu-id="e6b96-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6b96-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b96-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6b96-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6b96-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6b96-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6b96-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6b96-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
