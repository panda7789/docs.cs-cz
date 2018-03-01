---
title: "ICorDebugAppDomain::GetProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c1a488e3d1c4e3c8f95bb29d9fb30d41cda1b43f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="94de3-102">ICorDebugAppDomain::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="94de3-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="94de3-103">Získá proces obsahující domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="94de3-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94de3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94de3-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94de3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94de3-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="94de3-106">[out] Ukazatel na adresu ICorDebugProcess objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="94de3-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94de3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94de3-107">Requirements</span></span>  
 <span data-ttu-id="94de3-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94de3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94de3-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94de3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94de3-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94de3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94de3-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94de3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
