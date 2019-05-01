---
title: ICorDebugProcess::GetHelperThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987737"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="aaa7d-102">ICorDebugProcess::GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="aaa7d-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="aaa7d-103">Získá ID vlákna operačního systému (OS) interní pomocné vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaa7d-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaa7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaa7d-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="aaa7d-106">[out] Ukazatel na operační systém vlákna ID interní pomocné vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaa7d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaa7d-107">Remarks</span></span>  
 <span data-ttu-id="aaa7d-108">Při ladění spravované a nespravované, zodpovídá za ladicího programu k zajištění, že vlákno se zadaným ID zůstane spuštěný, pokud ho narazí na zarážku, umístí ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="aaa7d-109">Ladicí program může také chtít skrýt toto vlákno od uživatele.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="aaa7d-110">Pokud neexistuje žádný pomocné vlákno v procesu ještě, `GetHelperThreadID` metoda vrátí nulu v \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="aaa7d-111">ID vlákna pomocné vlákno nemůže mezipaměti, protože to může v průběhu času měnit.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="aaa7d-112">ID vlákna v každé události zastavení musíte znovu odeslán dotaz.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="aaa7d-113">ID vlákna pomocné vlákno ladicího programu bude správné na každý nespravované [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) událostí, což umožní ladicí program k určení ID vlákna z jeho pomocné vlákno a skryjte ji pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="aaa7d-114">Podproces, který je označen jako pomocné vlákno během nespravované `ICorDebugManagedCallback::CreateThread` událostí bude nespouštět spravovaného uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa7d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aaa7d-115">Requirements</span></span>  
 <span data-ttu-id="aaa7d-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa7d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa7d-117">**Záhlaví:** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="aaa7d-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="aaa7d-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aaa7d-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="aaa7d-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaa7d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaa7d-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa7d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
