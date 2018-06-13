---
title: ICorDebugChain::GetPrevious – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c0545440ed63ba914229249080ec9f6be8eb2b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402250"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="17b17-102">ICorDebugChain::GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="17b17-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="17b17-103">Získá předchozí řetěz snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="17b17-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17b17-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17b17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17b17-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="17b17-106">[out] Ukazatel na adresu ICorDebugChain objekt, který reprezentuje předchozího řetězce rámce pro tento přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="17b17-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="17b17-107">Pokud je tento řetězec řetězu první `ppChain` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="17b17-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17b17-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17b17-108">Requirements</span></span>  
 <span data-ttu-id="17b17-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17b17-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17b17-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17b17-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17b17-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17b17-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17b17-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b17-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
