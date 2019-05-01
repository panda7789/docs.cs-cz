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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994055"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="d2212-102">ICorDebugThread::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="d2212-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="d2212-103">Získá ukazatel rozhraní na tomto objektu ICorDebugThread na aktivní rámec (nejnovější).</span><span class="sxs-lookup"><span data-stu-id="d2212-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2212-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2212-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2212-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2212-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="d2212-106">[out] Ukazatel na adresu objektu icordebugframe – rozhraní, která představuje rámec.</span><span class="sxs-lookup"><span data-stu-id="d2212-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2212-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2212-107">Remarks</span></span>  
 <span data-ttu-id="d2212-108">`ppFrame` Parametr má hodnotu null, pokud žádný snímek není aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="d2212-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2212-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2212-109">Requirements</span></span>  
 <span data-ttu-id="d2212-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2212-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2212-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2212-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2212-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2212-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2212-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2212-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
