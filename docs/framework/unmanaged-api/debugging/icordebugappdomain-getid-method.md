---
title: ICorDebugAppDomain::GetId – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
ms.openlocfilehash: 87c43d6f05dffbf10ca1dd9253abfe893db9adf5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110483"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="ee286-102">ICorDebugAppDomain::GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="ee286-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="ee286-103">Získá jedinečný identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee286-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee286-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee286-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee286-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee286-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="ee286-106">mimo Jedinečný identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ee286-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee286-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee286-107">Remarks</span></span>  
 <span data-ttu-id="ee286-108">Identifikátor domény aplikace je jedinečný v rámci nadřazeného procesu.</span><span class="sxs-lookup"><span data-stu-id="ee286-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee286-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee286-109">Requirements</span></span>  
 <span data-ttu-id="ee286-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee286-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee286-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee286-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee286-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ee286-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee286-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee286-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
