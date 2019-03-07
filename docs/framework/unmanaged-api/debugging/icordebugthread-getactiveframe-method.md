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
ms.openlocfilehash: 051491173bbcef3d87d9a3dbe854eece46c49e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468777"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="18093-102">ICorDebugThread::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="18093-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="18093-103">Získá ukazatel rozhraní na tomto objektu ICorDebugThread na aktivní rámec (nejnovější).</span><span class="sxs-lookup"><span data-stu-id="18093-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18093-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18093-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18093-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18093-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="18093-106">[out] Ukazatel na adresu objektu icordebugframe – rozhraní, která představuje rámec.</span><span class="sxs-lookup"><span data-stu-id="18093-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18093-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18093-107">Remarks</span></span>  
 <span data-ttu-id="18093-108">`ppFrame` Parametr má hodnotu null, pokud žádný snímek není aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="18093-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18093-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18093-109">Requirements</span></span>  
 <span data-ttu-id="18093-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18093-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18093-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18093-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18093-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18093-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18093-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18093-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
