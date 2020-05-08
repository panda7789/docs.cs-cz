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
ms.openlocfilehash: eade3fd5d946c44ae4a77c571f762709de3cef40
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976561"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="90918-102">ICorDebugController::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="90918-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="90918-103">Ukončí proces se zadaným ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="90918-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90918-104">Tato metoda je obálkou pro funkci Win32 `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="90918-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="90918-105">Proto `Terminate` používá ukončovací kód stejným způsobem, jaký používá funkce Win32 `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="90918-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90918-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90918-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90918-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="90918-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="90918-108">pro Číselná hodnota, která je ukončovacím kódem.</span><span class="sxs-lookup"><span data-stu-id="90918-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="90918-109">Platné číselné hodnoty jsou definovány v Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="90918-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90918-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90918-110">Remarks</span></span>  
 <span data-ttu-id="90918-111">Pokud je `Terminate` proces zastaven při volání, proces by měl pokračovat pomocí metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , aby ladicí program přijal potvrzení ukončení prostřednictvím zpětného volání [ICorDebugManagedCallback:: ExitProcess –](icordebugmanagedcallback-exitprocess-method.md) nebo [ICorDebugManagedCallback:: ExitAppDomain –](icordebugmanagedcallback-exitappdomain-method.md) .</span><span class="sxs-lookup"><span data-stu-id="90918-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90918-112">Tato metoda není implementována doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="90918-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="90918-113">To znamená, že není implementován na <xref:System.AppDomain> úrovni.</span><span class="sxs-lookup"><span data-stu-id="90918-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90918-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90918-114">Requirements</span></span>  
 <span data-ttu-id="90918-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90918-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90918-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="90918-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90918-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="90918-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90918-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90918-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90918-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="90918-119">See also</span></span>
