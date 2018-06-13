---
title: ICorDebugThread::GetActiveFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a1bbe5674ba11b5ee6033c65f229d698eff15ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420638"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="289e3-102">ICorDebugThread::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="289e3-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="289e3-103">Získá ukazatele rozhraní na aktivní snímek (nejnovější) na tomto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="289e3-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="289e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="289e3-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="289e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="289e3-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="289e3-106">[out] Ukazatel na adresu ICorDebugFrame rozhraní objekt, který reprezentuje rámečku.</span><span class="sxs-lookup"><span data-stu-id="289e3-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="289e3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="289e3-107">Remarks</span></span>  
 <span data-ttu-id="289e3-108">`ppFrame` Parametr má hodnotu null, pokud je aktuálně aktivní žádné rámce.</span><span class="sxs-lookup"><span data-stu-id="289e3-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="289e3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="289e3-109">Requirements</span></span>  
 <span data-ttu-id="289e3-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="289e3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="289e3-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="289e3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="289e3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="289e3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="289e3-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="289e3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
