---
title: "ICorDebugInternalFrame2::GetFrameAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.GetFrameAddress Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ee867afe99fc5d2f2eb27bb1e6888aef8341d71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="9cb36-102">ICorDebugInternalFrame2::GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="9cb36-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="9cb36-103">Vrátí adresu zásobníku vnitřní rámečku.</span><span class="sxs-lookup"><span data-stu-id="9cb36-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cb36-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cb36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cb36-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="9cb36-106">[out] Ukazatel `CORDB_ADDRESS` pro vnitřní snímek.</span><span class="sxs-lookup"><span data-stu-id="9cb36-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cb36-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9cb36-107">Return Value</span></span>  
 <span data-ttu-id="9cb36-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="9cb36-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9cb36-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cb36-109">HRESULT</span></span>|<span data-ttu-id="9cb36-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9cb36-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cb36-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cb36-111">S_OK</span></span>|<span data-ttu-id="9cb36-112">Adresu interní rámce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9cb36-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="9cb36-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9cb36-113">E_FAIL</span></span>|<span data-ttu-id="9cb36-114">Nelze vrátit adresu interní rámce.</span><span class="sxs-lookup"><span data-stu-id="9cb36-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="9cb36-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9cb36-115">E_INVALIDARG</span></span>|<span data-ttu-id="9cb36-116">`pAddress`je `null`.</span><span class="sxs-lookup"><span data-stu-id="9cb36-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cb36-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cb36-117">Remarks</span></span>  
 <span data-ttu-id="9cb36-118">Hodnota vrácená v `pAddress` slouží k určení umístění interní rámečku relativně k jiné rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9cb36-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="9cb36-119">To i na platformu IA-64 počítačích interní rámečku žije v zásobníku pouze a neexistuje žádný odpovídající ukazatel k záložnímu úložišti.</span><span class="sxs-lookup"><span data-stu-id="9cb36-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb36-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cb36-120">Requirements</span></span>  
 <span data-ttu-id="9cb36-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cb36-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb36-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cb36-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cb36-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cb36-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cb36-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb36-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb36-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cb36-125">See Also</span></span>  
 [<span data-ttu-id="9cb36-126">Icordebuginternalframe2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cb36-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="9cb36-127">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cb36-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9cb36-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="9cb36-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
