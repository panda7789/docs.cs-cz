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
ms.openlocfilehash: bef51fe9df0f85659603c637f11ed4e856c8e01a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133956"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="cae4e-102">ICorDebugAssembly2::IsFullyTrusted – metoda</span><span class="sxs-lookup"><span data-stu-id="cae4e-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="cae4e-103">Získá hodnotu, která označuje, zda bylo sestavení uděleno úplnému vztahu důvěryhodnosti systémem zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cae4e-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cae4e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cae4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cae4e-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="cae4e-106">[out] `true`, pokud je sestavení uděleno úplnému vztahu důvěryhodnosti systémem zabezpečení modulu runtime; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="cae4e-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cae4e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cae4e-107">Remarks</span></span>  
 <span data-ttu-id="cae4e-108">Tato metoda vrátí hodnotu HRESULT prvku CORDBG_E_NOTREADY, pokud zásady zabezpečení pro sestavení ještě nebyly přeloženy, to znamená, pokud dosud nebyl spuštěn žádný kód v sestavení.</span><span class="sxs-lookup"><span data-stu-id="cae4e-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cae4e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cae4e-109">Requirements</span></span>  
 <span data-ttu-id="cae4e-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cae4e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae4e-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cae4e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cae4e-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cae4e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cae4e-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae4e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
