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
ms.openlocfilehash: 41b2e009f8f017a72147232015ea2357ae922ca1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793652"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="617dd-102">ICLRDebugging::CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="617dd-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="617dd-103">Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="617dd-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="617dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="617dd-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="617dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="617dd-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="617dd-106">pro Základní adresa modulu v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="617dd-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="617dd-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="617dd-107">Return Value</span></span>  
 <span data-ttu-id="617dd-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="617dd-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="617dd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="617dd-109">HRESULT</span></span>|<span data-ttu-id="617dd-110">Popis</span><span class="sxs-lookup"><span data-stu-id="617dd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="617dd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="617dd-111">S_OK</span></span>|<span data-ttu-id="617dd-112">Modul, na který odkazuje `hmodule`, může být uvolněn.</span><span class="sxs-lookup"><span data-stu-id="617dd-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="617dd-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="617dd-113">S_FALSE</span></span>|<span data-ttu-id="617dd-114">Modul, na který odkazuje `hmodule`, se stále používá.</span><span class="sxs-lookup"><span data-stu-id="617dd-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="617dd-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="617dd-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="617dd-116">Uvedený modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="617dd-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="617dd-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="617dd-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="617dd-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="617dd-118">Remarks</span></span>  
 <span data-ttu-id="617dd-119">Tato metoda kontroluje, zda byly uvolněny všechny instance rozhraní `ICorDebug*` a v současné době není v rámci volání metody [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="617dd-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="617dd-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="617dd-120">Requirements</span></span>  
 <span data-ttu-id="617dd-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="617dd-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="617dd-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="617dd-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="617dd-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="617dd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="617dd-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="617dd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617dd-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="617dd-125">See also</span></span>

- [<span data-ttu-id="617dd-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="617dd-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="617dd-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="617dd-127">Debugging</span></span>](index.md)
