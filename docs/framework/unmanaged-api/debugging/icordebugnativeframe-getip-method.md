---
title: "ICorDebugNativeFrame::GetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ceb0188ce2a52c3950b5fc89ea15c96852910d88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="664b0-102">ICorDebugNativeFrame::GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="664b0-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="664b0-103">Získá nativní kód posun umístění, ke které je aktuálně nastaven ukazatel instrukce.</span><span class="sxs-lookup"><span data-stu-id="664b0-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="664b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="664b0-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="664b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="664b0-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="664b0-106">[out] Ukazatel na umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="664b0-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="664b0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="664b0-107">Remarks</span></span>  
 <span data-ttu-id="664b0-108">Pokud rámce zásobníku, která je reprezentována tento "ICorDebugNativeFrame" je aktivní, posun je adresa instrukce další spuštění.</span><span class="sxs-lookup"><span data-stu-id="664b0-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="664b0-109">Pokud tento rámec zásobníku není aktivní, posun je adresa instrukce další budou spuštěny při opětovné aktivaci rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="664b0-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="664b0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="664b0-110">Requirements</span></span>  
 <span data-ttu-id="664b0-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="664b0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="664b0-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="664b0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="664b0-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="664b0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="664b0-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="664b0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664b0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="664b0-115">See Also</span></span>  
 
