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
ms.openlocfilehash: 65a374f942697ee670507987c4a97a7977970b69
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481089"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="d8478-102">ICorDebugController::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="d8478-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="d8478-103">Ukončí proces s uvedený ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="d8478-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8478-104">Tato metoda je obálka pro Win32 `TerminateProcess` funkce.</span><span class="sxs-lookup"><span data-stu-id="d8478-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="d8478-105">Proto `Terminate` používá ukončovací kód procesu ve stejném způsobu, jakým Win32 `TerminateProcess` funkce použije.</span><span class="sxs-lookup"><span data-stu-id="d8478-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8478-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8478-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8478-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8478-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="d8478-108">[in] Číselná hodnota, která je ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="d8478-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="d8478-109">Platné číselné hodnoty jsou definovány v Winbase.h.</span><span class="sxs-lookup"><span data-stu-id="d8478-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8478-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8478-110">Remarks</span></span>  
 <span data-ttu-id="d8478-111">Zastavení procesu, kdy `Terminate` je volána, proces by měly pokračovat s použitím [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metodu tak, aby ladicí program přijímá potvrzení ukončení prostřednictvím [ Icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) nebo [icordebugmanagedcallback::exitappdomain –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d8478-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8478-112">Tato metoda není implementována podle domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8478-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="d8478-113">To znamená, že není implementovaná v <xref:System.AppDomain> úroveň.</span><span class="sxs-lookup"><span data-stu-id="d8478-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8478-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8478-114">Requirements</span></span>  
 <span data-ttu-id="d8478-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8478-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8478-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8478-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8478-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8478-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8478-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8478-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8478-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8478-119">See also</span></span>

