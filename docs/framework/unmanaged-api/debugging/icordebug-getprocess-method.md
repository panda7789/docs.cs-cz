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
ms.openlocfilehash: dcb869bed71be05e0450580b50dfa9f2a0fca525
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169790"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="355d1-102">ICorDebug::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="355d1-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="355d1-103">Získá ukazatel na instanci "ICorDebugProcess" pro zadaný proces.</span><span class="sxs-lookup"><span data-stu-id="355d1-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="355d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="355d1-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="355d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="355d1-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="355d1-106">[in] ID procesu.</span><span class="sxs-lookup"><span data-stu-id="355d1-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="355d1-107">[out] Ukazatel na adresu `ICorDebugProcess` instance pro zadaný proces.</span><span class="sxs-lookup"><span data-stu-id="355d1-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="355d1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="355d1-108">Requirements</span></span>  
 <span data-ttu-id="355d1-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="355d1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="355d1-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="355d1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="355d1-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="355d1-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="355d1-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="355d1-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="355d1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="355d1-113">See also</span></span>

- [<span data-ttu-id="355d1-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="355d1-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
