---
title: "ICorDebugNativeFrame::CanSetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.CanSetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33b5efe6352d3a0c30179990205315c76f3a704d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="912e4-102">ICorDebugNativeFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="912e4-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="912e4-103">Získá HRESULT určující, zda je možné nastavit ukazatel instrukce (IP) do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="912e4-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="912e4-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="912e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="912e4-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="912e4-106">[v] Ukazatel instrukce požadované nastavení.</span><span class="sxs-lookup"><span data-stu-id="912e4-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="912e4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="912e4-107">Remarks</span></span>  
 <span data-ttu-id="912e4-108">Použití `CanSetIP` metoda před voláním [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="912e4-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="912e4-109">Pokud `CanSetIP` vrátí všechny HRESULT než S_OK, můžete stále vyvolat `ICorDebugNativeFrame::SetIP`, ale neexistuje žádná záruka, že bezpečné a správné spuštění kódu laděné bude pokračovat, ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="912e4-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912e4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="912e4-110">Requirements</span></span>  
 <span data-ttu-id="912e4-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="912e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912e4-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="912e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="912e4-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="912e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="912e4-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912e4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="912e4-115">See Also</span></span>  
 
