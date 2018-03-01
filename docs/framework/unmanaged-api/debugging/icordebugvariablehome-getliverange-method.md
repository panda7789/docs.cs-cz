---
title: "IcorDebugVariableHome::GetLiveRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bb86921be3398e6e9653838c1aec6b40ca86469
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="8ef43-102">IcorDebugVariableHome::GetLiveRange – metoda</span><span class="sxs-lookup"><span data-stu-id="8ef43-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="8ef43-103">Získá nativní rozsahu, za které je tato proměnná za provozu.</span><span class="sxs-lookup"><span data-stu-id="8ef43-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef43-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ef43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ef43-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="8ef43-106">[out] Logické posun, na které proměnné jsou první za provozu.</span><span class="sxs-lookup"><span data-stu-id="8ef43-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="8ef43-107">[out] Logické posun ihned po bodu, na které proměnné jsou poslední za provozu.</span><span class="sxs-lookup"><span data-stu-id="8ef43-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef43-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ef43-108">Requirements</span></span>  
 <span data-ttu-id="8ef43-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef43-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef43-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ef43-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ef43-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ef43-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ef43-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef43-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef43-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef43-113">See Also</span></span>  
 [<span data-ttu-id="8ef43-114">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef43-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
