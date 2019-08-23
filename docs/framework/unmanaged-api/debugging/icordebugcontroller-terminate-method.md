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
ms.openlocfilehash: ee1c30809567097e67b6b1e40f5534429d748abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964373"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="31273-102">ICorDebugController::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="31273-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="31273-103">Ukončí proces se zadaným ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="31273-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31273-104">Tato metoda je obálkou pro funkci Win32 `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="31273-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="31273-105">Proto používá ukončovací kód stejným způsobem, jaký používá funkce Win32 `TerminateProcess`. `Terminate`</span><span class="sxs-lookup"><span data-stu-id="31273-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31273-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31273-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31273-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="31273-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="31273-108">pro Číselná hodnota, která je ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="31273-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="31273-109">Platné číselné hodnoty jsou definovány v Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="31273-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31273-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31273-110">Remarks</span></span>  
 <span data-ttu-id="31273-111">Pokud je proces zastaven při `Terminate` volání, proces by měl pokračovat pomocí metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby ladicí program přijal potvrzení ukončení prostřednictvím [ICorDebugManagedCallback:: ExitProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) nebo [ICorDebugManagedCallback:: ExitAppDomain –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="31273-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31273-112">Tato metoda není implementována doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="31273-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="31273-113">To znamená, že není implementován na <xref:System.AppDomain> úrovni.</span><span class="sxs-lookup"><span data-stu-id="31273-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31273-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31273-114">Requirements</span></span>  
 <span data-ttu-id="31273-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31273-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31273-116">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31273-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31273-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31273-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31273-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31273-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31273-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31273-119">See also</span></span>
