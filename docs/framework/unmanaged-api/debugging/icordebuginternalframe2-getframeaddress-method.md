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
ms.openlocfilehash: 51c8f9a2b66d7b2553949056f7cdbedcf5ea37d6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209913"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="9794d-102">ICorDebugInternalFrame2::GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="9794d-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="9794d-103">Vrátí adresu zásobníku interního rámce.</span><span class="sxs-lookup"><span data-stu-id="9794d-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9794d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9794d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9794d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9794d-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="9794d-106">mimo Ukazatel na `CORDB_ADDRESS` vnitřní rámec.</span><span class="sxs-lookup"><span data-stu-id="9794d-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9794d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9794d-107">Return Value</span></span>  
 <span data-ttu-id="9794d-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="9794d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9794d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9794d-109">HRESULT</span></span>|<span data-ttu-id="9794d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9794d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9794d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9794d-111">S_OK</span></span>|<span data-ttu-id="9794d-112">Adresa interního rámce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9794d-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="9794d-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9794d-113">E_FAIL</span></span>|<span data-ttu-id="9794d-114">Adresa interního rámce nemohla být vrácena.</span><span class="sxs-lookup"><span data-stu-id="9794d-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="9794d-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9794d-115">E_INVALIDARG</span></span>|<span data-ttu-id="9794d-116">`pAddress` je `null`.</span><span class="sxs-lookup"><span data-stu-id="9794d-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9794d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9794d-117">Remarks</span></span>  
 <span data-ttu-id="9794d-118">Hodnota vrácená v rámci `pAddress` lze použít k určení umístění vnitřního rámce relativně k ostatním snímkům v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9794d-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="9794d-119">I na počítačích založených na platformě IA-64, interním rámcům v zásobníku a neexistuje žádný odpovídající ukazatel na záložní úložiště.</span><span class="sxs-lookup"><span data-stu-id="9794d-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9794d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9794d-120">Requirements</span></span>  
 <span data-ttu-id="9794d-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9794d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9794d-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9794d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9794d-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9794d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9794d-124">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9794d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9794d-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9794d-125">See also</span></span>

- [<span data-ttu-id="9794d-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9794d-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="9794d-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9794d-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9794d-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="9794d-128">Debugging</span></span>](index.md)
