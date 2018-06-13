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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7a95f09d1baebed65bae994550431d88ba0dfc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412468"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="62396-102">ICorDebugController::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="62396-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="62396-103">Ukončí proces uvedený ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="62396-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62396-104">Tato metoda je obálka pro Win32 `TerminateProcess` funkce.</span><span class="sxs-lookup"><span data-stu-id="62396-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="62396-105">Proto `Terminate` používá ukončovací kód ve stejném způsobem Win32 `TerminateProcess` funkce používá je.</span><span class="sxs-lookup"><span data-stu-id="62396-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62396-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62396-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62396-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="62396-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="62396-108">[v] Číselnou hodnotu, která je v něm ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="62396-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="62396-109">Platné číselné hodnoty jsou definovány v Winbase.h.</span><span class="sxs-lookup"><span data-stu-id="62396-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62396-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62396-110">Remarks</span></span>  
 <span data-ttu-id="62396-111">Po zastavení procesu, při `Terminate` je volána, by měly pokračovat proces, pomocí [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metoda tak, aby ladicí program obdržel potvrzení ukončení prostřednictvím [ Icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) nebo [icordebugmanagedcallback::exitappdomain –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="62396-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62396-112">Tato metoda není implementována podle domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="62396-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="62396-113">To znamená, není implementována v <xref:System.AppDomain> úroveň.</span><span class="sxs-lookup"><span data-stu-id="62396-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62396-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62396-114">Requirements</span></span>  
 <span data-ttu-id="62396-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62396-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62396-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62396-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62396-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62396-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62396-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62396-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62396-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="62396-119">See Also</span></span>  
 
