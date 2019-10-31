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
ms.openlocfilehash: 40e64bdb35cff4e6ad6132c0806cfddd2767443c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122678"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="aa32c-102">ICorDebugInternalFrame2::GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="aa32c-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="aa32c-103">Vrátí adresu zásobníku interního rámce.</span><span class="sxs-lookup"><span data-stu-id="aa32c-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa32c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa32c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa32c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa32c-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="aa32c-106">mimo Ukazatel na `CORDB_ADDRESS` pro vnitřní rámec.</span><span class="sxs-lookup"><span data-stu-id="aa32c-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa32c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa32c-107">Return Value</span></span>  
 <span data-ttu-id="aa32c-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="aa32c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aa32c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa32c-109">HRESULT</span></span>|<span data-ttu-id="aa32c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="aa32c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa32c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa32c-111">S_OK</span></span>|<span data-ttu-id="aa32c-112">Adresa interního rámce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="aa32c-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="aa32c-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa32c-113">E_FAIL</span></span>|<span data-ttu-id="aa32c-114">Adresa interního rámce nemohla být vrácena.</span><span class="sxs-lookup"><span data-stu-id="aa32c-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="aa32c-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="aa32c-115">E_INVALIDARG</span></span>|<span data-ttu-id="aa32c-116">`pAddress` je `null`.</span><span class="sxs-lookup"><span data-stu-id="aa32c-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa32c-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa32c-117">Remarks</span></span>  
 <span data-ttu-id="aa32c-118">Hodnota vrácená v `pAddress` lze použít k určení umístění vnitřního rámce relativně k ostatním snímkům v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aa32c-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="aa32c-119">I na počítačích založených na platformě IA-64, interním rámcům v zásobníku a neexistuje žádný odpovídající ukazatel na záložní úložiště.</span><span class="sxs-lookup"><span data-stu-id="aa32c-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa32c-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa32c-120">Requirements</span></span>  
 <span data-ttu-id="aa32c-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa32c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa32c-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa32c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa32c-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aa32c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa32c-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa32c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa32c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa32c-125">See also</span></span>

- [<span data-ttu-id="aa32c-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa32c-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="aa32c-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="aa32c-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aa32c-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="aa32c-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
