---
title: ICorDebug::GetProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e04bef30d4a9edf9898b27e15a79b2b70e3a7f31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477853"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="c6850-102">ICorDebug::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="c6850-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="c6850-103">Získá ukazatel na instanci "ICorDebugProcess" pro zadaný proces.</span><span class="sxs-lookup"><span data-stu-id="c6850-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6850-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6850-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6850-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6850-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="c6850-106">[in] ID procesu.</span><span class="sxs-lookup"><span data-stu-id="c6850-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c6850-107">[out] Ukazatel na adresu `ICorDebugProcess` instance pro zadaný proces.</span><span class="sxs-lookup"><span data-stu-id="c6850-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6850-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6850-108">Requirements</span></span>  
 <span data-ttu-id="c6850-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6850-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6850-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6850-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6850-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6850-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6850-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6850-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6850-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6850-113">See also</span></span>
- [<span data-ttu-id="c6850-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6850-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
