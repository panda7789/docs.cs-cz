---
title: "ICorDebugFrame::GetFunctionToken – metoda"
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
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d36606dfffb6ff5872ee88f00d3d94f3ececce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="bf830-102">ICorDebugFrame::GetFunctionToken – metoda</span><span class="sxs-lookup"><span data-stu-id="bf830-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="bf830-103">Získá metadata token pro funkce, která obsahuje kód přidružené k této rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bf830-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf830-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf830-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf830-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf830-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="bf830-106">[out] Ukazatel na `mdMethodDef` token, který odkazuje na metadata pro funkci.</span><span class="sxs-lookup"><span data-stu-id="bf830-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf830-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf830-107">Requirements</span></span>  
 <span data-ttu-id="bf830-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf830-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf830-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf830-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf830-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf830-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf830-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf830-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
