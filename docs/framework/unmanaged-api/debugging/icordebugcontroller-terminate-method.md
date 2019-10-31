---
title: ICorDebugController::Terminate – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: fb8cfb2d1c5902ecd0d5858ef21ba48b65b12506
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125331"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="64fac-102">ICorDebugController::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="64fac-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="64fac-103">Ukončí proces se zadaným ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="64fac-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64fac-104">Tato metoda je obálkou pro funkci Win32 `TerminateProcess`.</span><span class="sxs-lookup"><span data-stu-id="64fac-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="64fac-105">Proto `Terminate` používá ukončovací kód stejným způsobem, jakým používá funkce Win32 `TerminateProcess`.</span><span class="sxs-lookup"><span data-stu-id="64fac-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64fac-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64fac-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64fac-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="64fac-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="64fac-108">pro Číselná hodnota, která je ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="64fac-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="64fac-109">Platné číselné hodnoty jsou definovány v Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="64fac-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64fac-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64fac-110">Remarks</span></span>  
 <span data-ttu-id="64fac-111">Pokud je proces zastaven při volání `Terminate`, proces by měl pokračovat pomocí metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby ladicí program přijal potvrzení ukončení prostřednictvím [ICorDebugManagedCallback:: ExitProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) nebo [ICorDebugManagedCallback:: ExitAppDomain –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="64fac-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64fac-112">Tato metoda není implementována doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="64fac-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="64fac-113">To znamená, že není implementován na úrovni <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="64fac-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64fac-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64fac-114">Requirements</span></span>  
 <span data-ttu-id="64fac-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64fac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64fac-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64fac-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64fac-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="64fac-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64fac-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64fac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fac-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64fac-119">See also</span></span>
