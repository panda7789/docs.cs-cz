---
title: ICLRDebugging::CanUnloadNow – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: 4eb6682ac5a8b7788d97f752f249d85886fba0b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111653"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="ccbec-102">ICLRDebugging::CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="ccbec-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="ccbec-103">Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="ccbec-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccbec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccbec-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccbec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccbec-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="ccbec-106">pro Základní adresa modulu v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="ccbec-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccbec-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ccbec-107">Return Value</span></span>  
 <span data-ttu-id="ccbec-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="ccbec-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ccbec-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ccbec-109">HRESULT</span></span>|<span data-ttu-id="ccbec-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ccbec-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ccbec-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ccbec-111">S_OK</span></span>|<span data-ttu-id="ccbec-112">Modul, na který odkazuje `hmodule`, může být uvolněn.</span><span class="sxs-lookup"><span data-stu-id="ccbec-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="ccbec-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ccbec-113">S_FALSE</span></span>|<span data-ttu-id="ccbec-114">Modul, na který odkazuje `hmodule`, se stále používá.</span><span class="sxs-lookup"><span data-stu-id="ccbec-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="ccbec-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="ccbec-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="ccbec-116">Uvedený modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="ccbec-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ccbec-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="ccbec-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccbec-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccbec-118">Remarks</span></span>  
 <span data-ttu-id="ccbec-119">Tato metoda kontroluje, zda byly uvolněny všechny instance rozhraní `ICorDebug*` a v současné době není v rámci volání metody [ICLRDebugging:: OpenVirtualProcess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="ccbec-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccbec-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccbec-120">Requirements</span></span>  
 <span data-ttu-id="ccbec-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccbec-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccbec-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ccbec-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccbec-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ccbec-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccbec-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccbec-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbec-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccbec-125">See also</span></span>

- [<span data-ttu-id="ccbec-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ccbec-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ccbec-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="ccbec-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
