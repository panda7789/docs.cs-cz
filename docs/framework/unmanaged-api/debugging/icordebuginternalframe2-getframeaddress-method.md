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
ms.workload: dotnet
ms.openlocfilehash: f44f0707892197398e4638a5e6d037fba7c8fc71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="02330-102">ICorDebugInternalFrame2::GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="02330-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="02330-103">Vrátí adresu zásobníku vnitřní rámečku.</span><span class="sxs-lookup"><span data-stu-id="02330-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02330-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02330-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02330-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02330-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="02330-106">[out] Ukazatel `CORDB_ADDRESS` pro vnitřní snímek.</span><span class="sxs-lookup"><span data-stu-id="02330-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02330-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="02330-107">Return Value</span></span>  
 <span data-ttu-id="02330-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="02330-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="02330-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02330-109">HRESULT</span></span>|<span data-ttu-id="02330-110">Popis</span><span class="sxs-lookup"><span data-stu-id="02330-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02330-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="02330-111">S_OK</span></span>|<span data-ttu-id="02330-112">Adresu interní rámce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="02330-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="02330-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="02330-113">E_FAIL</span></span>|<span data-ttu-id="02330-114">Nelze vrátit adresu interní rámce.</span><span class="sxs-lookup"><span data-stu-id="02330-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="02330-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="02330-115">E_INVALIDARG</span></span>|<span data-ttu-id="02330-116">`pAddress`je `null`.</span><span class="sxs-lookup"><span data-stu-id="02330-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02330-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02330-117">Remarks</span></span>  
 <span data-ttu-id="02330-118">Hodnota vrácená v `pAddress` slouží k určení umístění interní rámečku relativně k jiné rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="02330-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="02330-119">To i na platformu IA-64 počítačích interní rámečku žije v zásobníku pouze a neexistuje žádný odpovídající ukazatel k záložnímu úložišti.</span><span class="sxs-lookup"><span data-stu-id="02330-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02330-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02330-120">Requirements</span></span>  
 <span data-ttu-id="02330-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02330-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02330-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02330-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02330-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02330-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02330-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02330-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02330-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="02330-125">See Also</span></span>  
 [<span data-ttu-id="02330-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02330-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="02330-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="02330-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="02330-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="02330-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
