---
title: "ICorDebugFrame::GetChain – metoda"
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
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 479ad2db4752f9e031783b430396286c6989b115
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="77d69-102">ICorDebugFrame::GetChain – metoda</span><span class="sxs-lookup"><span data-stu-id="77d69-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="77d69-103">Získá ukazatel na řetězec, který je součástí tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="77d69-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77d69-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77d69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77d69-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="77d69-106">[out] Ukazatel na adresu ICorDebugChain objekt, který představuje řetězec obsahující tento snímek.</span><span class="sxs-lookup"><span data-stu-id="77d69-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d69-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77d69-107">Requirements</span></span>  
 <span data-ttu-id="77d69-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77d69-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d69-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77d69-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77d69-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77d69-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77d69-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d69-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
