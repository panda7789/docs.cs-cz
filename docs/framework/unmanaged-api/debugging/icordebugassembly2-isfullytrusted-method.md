---
title: "ICorDebugAssembly2::IsFullyTrusted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly2.IsFullyTrusted
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d155a12a8b281e427f00706cbc6e10a80804c7c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="c4dca-102">ICorDebugAssembly2::IsFullyTrusted – metoda</span><span class="sxs-lookup"><span data-stu-id="c4dca-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="c4dca-103">Získá hodnotu, která určuje, zda je sestavení bylo uděleno úplný vztah důvěryhodnosti v systému zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c4dca-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4dca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4dca-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4dca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4dca-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="c4dca-106">[out] `true` Pokud sestavení byl přidělen úplný vztah důvěryhodnosti systémem zabezpečení modulu runtime; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="c4dca-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4dca-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4dca-107">Remarks</span></span>  
 <span data-ttu-id="c4dca-108">Tato metoda vrátí dosud nebyla spuštěna HRESULT z CORDBG_E_NOTREADY Pokud zásady zabezpečení pro sestavení ještě nebyl vyřešen, to znamená, pokud žádný kód v sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4dca-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4dca-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4dca-109">Requirements</span></span>  
 <span data-ttu-id="c4dca-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4dca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4dca-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4dca-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4dca-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4dca-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4dca-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4dca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
