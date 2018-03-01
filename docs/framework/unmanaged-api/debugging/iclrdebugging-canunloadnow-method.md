---
title: "ICLRDebugging::CanUnloadNow – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b781db409991b07463002008a834dfb7ac32c9e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="b5687-102">ICLRDebugging::CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="b5687-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="b5687-103">Určuje, zda knihovnu, která byla vydána v [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní je stále používáno nebo může být odpojen.</span><span class="sxs-lookup"><span data-stu-id="b5687-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5687-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5687-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5687-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5687-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="b5687-106">[v] Základní adresa modulu v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="b5687-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5687-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5687-107">Return Value</span></span>  
 <span data-ttu-id="b5687-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="b5687-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b5687-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5687-109">HRESULT</span></span>|<span data-ttu-id="b5687-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b5687-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5687-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5687-111">S_OK</span></span>|<span data-ttu-id="b5687-112">Modul, který je odkazován objektem `hmodule` může být odpojen.</span><span class="sxs-lookup"><span data-stu-id="b5687-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="b5687-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b5687-113">S_FALSE</span></span>|<span data-ttu-id="b5687-114">Modul, který je odkazován objektem `hmodule` je stále používáno.</span><span class="sxs-lookup"><span data-stu-id="b5687-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="b5687-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="b5687-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="b5687-116">Modul uvedené není modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b5687-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b5687-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b5687-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5687-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5687-118">Remarks</span></span>  
 <span data-ttu-id="b5687-119">Tato metoda zkontroluje, zda všechny instance `ICorDebug*` byly vydány rozhraní a žádné vlákno je aktuálně v rámci volání [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="b5687-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5687-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5687-120">Requirements</span></span>  
 <span data-ttu-id="b5687-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5687-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5687-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5687-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5687-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5687-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5687-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5687-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5687-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5687-125">See Also</span></span>  
 [<span data-ttu-id="b5687-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b5687-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b5687-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="b5687-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
