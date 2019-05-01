---
title: ICorDebugInternalFrame2::GetFrameAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c30115a23f7f73662c9b3f4f4a09d45478ad687
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995472"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="3f376-102">ICorDebugInternalFrame2::GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="3f376-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="3f376-103">Vrátí adresu vnitřní rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3f376-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f376-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f376-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f376-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f376-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="3f376-106">[out] Ukazatel `CORDB_ADDRESS` pro vnitřní snímek.</span><span class="sxs-lookup"><span data-stu-id="3f376-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f376-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3f376-107">Return Value</span></span>  
 <span data-ttu-id="3f376-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="3f376-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3f376-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f376-109">HRESULT</span></span>|<span data-ttu-id="3f376-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3f376-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f376-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f376-111">S_OK</span></span>|<span data-ttu-id="3f376-112">Adresu vnitřní rámec byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3f376-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="3f376-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f376-113">E_FAIL</span></span>|<span data-ttu-id="3f376-114">Adresu vnitřní rámec nebylo možné vrátit.</span><span class="sxs-lookup"><span data-stu-id="3f376-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="3f376-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3f376-115">E_INVALIDARG</span></span>|<span data-ttu-id="3f376-116">`pAddress` je `null`.</span><span class="sxs-lookup"><span data-stu-id="3f376-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f376-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f376-117">Remarks</span></span>  
 <span data-ttu-id="3f376-118">Hodnota vrácená v `pAddress` slouží k určení umístění vnitřní rámec vzhledem k jiné rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3f376-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="3f376-119">I v počítačích pro platformu IA-64 vnitřní rámec může fungovat pouze do zásobníku a neexistuje žádný odpovídající ukazatel záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="3f376-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f376-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f376-120">Requirements</span></span>  
 <span data-ttu-id="3f376-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f376-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f376-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f376-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f376-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f376-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f376-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f376-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f376-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f376-125">See also</span></span>

- [<span data-ttu-id="3f376-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f376-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="3f376-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3f376-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3f376-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="3f376-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
