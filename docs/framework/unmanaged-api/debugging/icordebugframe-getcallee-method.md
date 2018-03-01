---
title: "ICorDebugFrame::GetCallee – metoda"
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
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 079d598e54f429fa4dd0b5c0c4cadbe2c66c1d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="e3029-102">ICorDebugFrame::GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="e3029-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="e3029-103">Získá ukazatel na objekt ICorDebugFrame v aktuální řetězec, který volá tento snímek.</span><span class="sxs-lookup"><span data-stu-id="e3029-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3029-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3029-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3029-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3029-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="e3029-106">[out] Ukazatel na adresu `ICorDebugFrame` objekt, který reprezentuje volané rámečku.</span><span class="sxs-lookup"><span data-stu-id="e3029-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="e3029-107">Tato hodnota je null, pokud je volání rámečku nejvnitřnější rámečku v řetězu aktuální.</span><span class="sxs-lookup"><span data-stu-id="e3029-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3029-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3029-108">Requirements</span></span>  
 <span data-ttu-id="e3029-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3029-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3029-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3029-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3029-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3029-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3029-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3029-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
