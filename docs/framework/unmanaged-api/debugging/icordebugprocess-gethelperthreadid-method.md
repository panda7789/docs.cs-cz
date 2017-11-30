---
title: "ICorDebugProcess::GetHelperThreadID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 092e99cb1d5534cee56db08b5a2eedaaa2fc4724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="d0627-102">ICorDebugProcess::GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="d0627-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="d0627-103">Získá ID vlákna operační systém (OS) ladicího programu interní pomocná přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="d0627-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0627-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0627-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0627-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0627-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="d0627-106">[out] Ukazatel na operačního systému thread ID vlákna interní pomocná ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="d0627-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0627-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0627-107">Remarks</span></span>  
 <span data-ttu-id="d0627-108">Během ladění spravovanými a nespravovanými, je odpovědností ladicího programu zajistit, že vlákno se zadaným ID zůstane spuštěný, pokud volání zarážku umístěna pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="d0627-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="d0627-109">Ladicí program také chtít skrýt tohoto podprocesu od uživatele.</span><span class="sxs-lookup"><span data-stu-id="d0627-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="d0627-110">Pokud existuje žádné pomocná přístup z více vláken v procesu ještě `GetHelperThreadID` metoda vrátí hodnotu nula v *`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="d0627-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in *`pThreadID`.</span></span>  
  
 <span data-ttu-id="d0627-111">ID vlákna vlákno pomocné rutiny, nelze mezipaměti, protože můžou časem změnit.</span><span class="sxs-lookup"><span data-stu-id="d0627-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="d0627-112">ID vlákna v každé události zastavení musí znovu zadat dotaz.</span><span class="sxs-lookup"><span data-stu-id="d0627-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="d0627-113">ID vlákna vlákno pomocná ladicího programu bude správné na každý nespravované [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) událostí, což umožňuje ladicí program určete ID vlákna jeho pomocné rutiny přístup z více vláken a skrýt od uživatele.</span><span class="sxs-lookup"><span data-stu-id="d0627-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="d0627-114">Podproces, který je označený pomocná vlákno během nespravované `ICorDebugManagedCallback::CreateThread` událostí nikdy spustí kód spravované uživatele.</span><span class="sxs-lookup"><span data-stu-id="d0627-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0627-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0627-115">Requirements</span></span>  
 <span data-ttu-id="d0627-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0627-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0627-117">**Záhlaví:** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="d0627-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="d0627-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0627-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="d0627-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0627-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0627-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0627-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
