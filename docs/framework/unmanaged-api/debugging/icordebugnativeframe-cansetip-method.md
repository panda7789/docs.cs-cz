---
title: "ICorDebugNativeFrame::CanSetIP – metoda"
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
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b87ff9ae71b916a9a1141c2e5fedce7f79fbcd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="fb92a-102">ICorDebugNativeFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="fb92a-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="fb92a-103">Získá HRESULT určující, zda je možné nastavit ukazatel instrukce (IP) do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="fb92a-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb92a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb92a-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb92a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb92a-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="fb92a-106">[v] Ukazatel instrukce požadované nastavení.</span><span class="sxs-lookup"><span data-stu-id="fb92a-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb92a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb92a-107">Remarks</span></span>  
 <span data-ttu-id="fb92a-108">Použití `CanSetIP` metoda před voláním [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="fb92a-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="fb92a-109">Pokud `CanSetIP` vrátí všechny HRESULT než S_OK, můžete stále vyvolat `ICorDebugNativeFrame::SetIP`, ale neexistuje žádná záruka, že bezpečné a správné spuštění kódu laděné bude pokračovat, ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fb92a-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb92a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb92a-110">Requirements</span></span>  
 <span data-ttu-id="fb92a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb92a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb92a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb92a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb92a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb92a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb92a-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb92a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb92a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb92a-115">See Also</span></span>  
 
