---
title: ICorDebugFrame::GetChain – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 032c1e3dcfe50cd30953ca581ff9f0d83b78518d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488467"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="be478-102">ICorDebugFrame::GetChain – metoda</span><span class="sxs-lookup"><span data-stu-id="be478-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="be478-103">Získá ukazatel na řetězec, který je součástí tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="be478-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be478-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be478-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be478-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be478-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="be478-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje řetězec obsahující tento rámec.</span><span class="sxs-lookup"><span data-stu-id="be478-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be478-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be478-107">Requirements</span></span>  
 <span data-ttu-id="be478-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be478-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be478-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be478-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be478-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be478-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be478-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be478-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
