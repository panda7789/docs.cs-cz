---
title: ICorDebugAssembly2::IsFullyTrusted – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd3b977a894f8cb1fc9a866f5a43265d917db513
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494438"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="d8824-102">ICorDebugAssembly2::IsFullyTrusted – metoda</span><span class="sxs-lookup"><span data-stu-id="d8824-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="d8824-103">Získá hodnotu určující, zda sestavení byla udělena úplná důvěryhodnost systém zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d8824-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8824-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8824-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8824-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8824-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="d8824-106">[out] `true` Pokud sestavení má byla udělena úplná důvěryhodnost systém zabezpečení modulu runtime; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="d8824-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8824-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8824-107">Remarks</span></span>  
 <span data-ttu-id="d8824-108">Tato metoda vrátí dosud byl spuštěn hodnotou HRESULT z CORDBG_E_NOTREADY Pokud zásady zabezpečení pro sestavení ještě nebyl vyřešen, to znamená, pokud žádný kód v sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8824-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8824-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8824-109">Requirements</span></span>  
 <span data-ttu-id="d8824-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8824-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8824-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8824-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8824-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8824-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8824-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8824-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
