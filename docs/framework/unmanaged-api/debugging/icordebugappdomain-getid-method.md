---
title: "ICorDebugAppDomain::GetId – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetId
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a8dcbc1fd710513b2b27e92f4d2e1e1b5c72092
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="96b20-102">ICorDebugAppDomain::GetId – metoda</span><span class="sxs-lookup"><span data-stu-id="96b20-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="96b20-103">Získá jedinečný identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="96b20-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96b20-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96b20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96b20-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="96b20-106">[out] Jedinečný identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="96b20-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96b20-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96b20-107">Remarks</span></span>  
 <span data-ttu-id="96b20-108">Je v rámci procesu obsahující jedinečný identifikátor pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="96b20-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b20-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96b20-109">Requirements</span></span>  
 <span data-ttu-id="96b20-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b20-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b20-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96b20-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96b20-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96b20-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96b20-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b20-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
