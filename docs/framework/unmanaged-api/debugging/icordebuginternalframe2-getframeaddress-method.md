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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187288"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="83bdf-102">ICorDebugInternalFrame2::GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="83bdf-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="83bdf-103">Vrátí adresu vnitřní rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="83bdf-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83bdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83bdf-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83bdf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83bdf-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="83bdf-106">[out] Ukazatel `CORDB_ADDRESS` pro vnitřní snímek.</span><span class="sxs-lookup"><span data-stu-id="83bdf-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83bdf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83bdf-107">Return Value</span></span>  
 <span data-ttu-id="83bdf-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="83bdf-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="83bdf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83bdf-109">HRESULT</span></span>|<span data-ttu-id="83bdf-110">Popis</span><span class="sxs-lookup"><span data-stu-id="83bdf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83bdf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="83bdf-111">S_OK</span></span>|<span data-ttu-id="83bdf-112">Adresu vnitřní rámec byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="83bdf-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="83bdf-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83bdf-113">E_FAIL</span></span>|<span data-ttu-id="83bdf-114">Adresu vnitřní rámec nebylo možné vrátit.</span><span class="sxs-lookup"><span data-stu-id="83bdf-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="83bdf-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="83bdf-115">E_INVALIDARG</span></span>|`pAddress` <span data-ttu-id="83bdf-116">is `null`.</span><span class="sxs-lookup"><span data-stu-id="83bdf-116">is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83bdf-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83bdf-117">Remarks</span></span>  
 <span data-ttu-id="83bdf-118">Hodnota vrácená v `pAddress` slouží k určení umístění vnitřní rámec vzhledem k jiné rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="83bdf-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="83bdf-119">I v počítačích pro platformu IA-64 vnitřní rámec může fungovat pouze do zásobníku a neexistuje žádný odpovídající ukazatel záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="83bdf-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83bdf-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83bdf-120">Requirements</span></span>  
 <span data-ttu-id="83bdf-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83bdf-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83bdf-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83bdf-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83bdf-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83bdf-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="83bdf-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="83bdf-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83bdf-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83bdf-125">See also</span></span>

- [<span data-ttu-id="83bdf-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83bdf-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="83bdf-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83bdf-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="83bdf-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="83bdf-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
