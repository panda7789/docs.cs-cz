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
ms.openlocfilehash: 9a4cf1f9ea1ccb174b5fb9336040d5e168653fb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088278"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="f1291-102">ICorDebugArrayValue::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="f1291-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="f1291-103">Získá počet rozměrů v poli.</span><span class="sxs-lookup"><span data-stu-id="f1291-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1291-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1291-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1291-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1291-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="f1291-106">mimo Ukazatel na počet dimenzí v tomto objektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="f1291-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1291-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1291-107">Requirements</span></span>  
 <span data-ttu-id="f1291-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1291-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1291-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f1291-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1291-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f1291-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1291-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1291-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
