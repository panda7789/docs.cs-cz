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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0aefc19ca0c255c9c8ea40fcc12fc5cba1b00f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501438"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="c61e6-102">ICorDebugAppDomain::GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="c61e6-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="c61e6-103">Získá jedinečný identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c61e6-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c61e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c61e6-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c61e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c61e6-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="c61e6-106">[out] Jedinečný identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c61e6-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c61e6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c61e6-107">Remarks</span></span>  
 <span data-ttu-id="c61e6-108">Identifikátor pro doménu aplikace je jedinečný v rámci nadřazeného procesu.</span><span class="sxs-lookup"><span data-stu-id="c61e6-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c61e6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c61e6-109">Requirements</span></span>  
 <span data-ttu-id="c61e6-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c61e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c61e6-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c61e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c61e6-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c61e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c61e6-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c61e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
