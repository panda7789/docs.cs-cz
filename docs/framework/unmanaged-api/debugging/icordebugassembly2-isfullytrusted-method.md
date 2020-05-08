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
ms.openlocfilehash: dd82709064fe7f7d912d93f4b3f0248769f02b9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894887"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="7c6e8-102">ICorDebugAssembly2::IsFullyTrusted – metoda</span><span class="sxs-lookup"><span data-stu-id="7c6e8-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="7c6e8-103">Získá hodnotu, která označuje, zda bylo sestavení uděleno úplnému vztahu důvěryhodnosti systémem zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7c6e8-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c6e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c6e8-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c6e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c6e8-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="7c6e8-106">mimo `true` Pokud byla sestavení udělena plná důvěryhodnost systémem zabezpečení modulu runtime; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="7c6e8-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c6e8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c6e8-107">Remarks</span></span>  
 <span data-ttu-id="7c6e8-108">Tato metoda vrací hodnotu HRESULT CORDBG_E_NOTREADY, pokud zásady zabezpečení pro sestavení ještě nebyly přeloženy, tj., pokud dosud nebyl spuštěn žádný kód v sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c6e8-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c6e8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c6e8-109">Requirements</span></span>  
 <span data-ttu-id="7c6e8-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c6e8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c6e8-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c6e8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c6e8-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7c6e8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c6e8-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c6e8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
