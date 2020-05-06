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
ms.openlocfilehash: 16d15101534b88d7da4093dab73b48b5c09a192c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860398"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="2a397-102">ICLRDebugging::CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="2a397-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="2a397-103">Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="2a397-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a397-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a397-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a397-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a397-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="2a397-106">pro Základní adresa modulu v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="2a397-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a397-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2a397-107">Return Value</span></span>  
 <span data-ttu-id="2a397-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="2a397-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2a397-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a397-109">HRESULT</span></span>|<span data-ttu-id="2a397-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2a397-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a397-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a397-111">S_OK</span></span>|<span data-ttu-id="2a397-112">Modul, na který je odkazováno, `hmodule` může být uvolněn.</span><span class="sxs-lookup"><span data-stu-id="2a397-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="2a397-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2a397-113">S_FALSE</span></span>|<span data-ttu-id="2a397-114">Modul, na který se odkazuje `hmodule` , se stále používá.</span><span class="sxs-lookup"><span data-stu-id="2a397-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="2a397-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="2a397-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="2a397-116">Uvedený modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="2a397-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2a397-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="2a397-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a397-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a397-118">Remarks</span></span>  
 <span data-ttu-id="2a397-119">Tato metoda kontroluje, zda byly uvolněny všechny `ICorDebug*` instance rozhraní a v současné době není v rámci volání metody [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) žádné vlákno.</span><span class="sxs-lookup"><span data-stu-id="2a397-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a397-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a397-120">Requirements</span></span>  
 <span data-ttu-id="2a397-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a397-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a397-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a397-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a397-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2a397-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a397-124">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a397-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a397-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a397-125">See also</span></span>

- [<span data-ttu-id="2a397-126">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a397-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2a397-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="2a397-127">Debugging</span></span>](index.md)
