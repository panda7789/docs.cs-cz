---
title: ICorDebugProcess::IsOSSuspended – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755456"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="996c5-102">ICorDebugProcess::IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="996c5-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="996c5-103">Získá hodnotu určující, zda zadaná vlákna se pozastavilo, v důsledku ukončení tohoto procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="996c5-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="996c5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="996c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="996c5-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="996c5-106">[in] ID vlákna nejistá.</span><span class="sxs-lookup"><span data-stu-id="996c5-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="996c5-107">[out] Ukazatel na logickou hodnotu, která je `true` Pokud vlákna zadaného byl pozastavený, jinak \*`pbSuspended` je `false`.</span><span class="sxs-lookup"><span data-stu-id="996c5-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996c5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="996c5-108">Remarks</span></span>  
 <span data-ttu-id="996c5-109">Když zadaného vlákna se pozastavilo, v důsledku ukončení tohoto procesu ladicího programu, zadané vlákno Win32 pozastavit počet se zvýší o jedna.</span><span class="sxs-lookup"><span data-stu-id="996c5-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="996c5-110">Uživatelské rozhraní (UI) ladicí program může být vhodné vzít v úvahu tyto informace pokud zobrazí operační systém (OS) pozastavit počet vláken pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="996c5-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="996c5-111">`IsOSSuspended` Metoda má smysl pouze v kontextu ladění nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="996c5-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="996c5-112">Při ladění spravovaných vláken jsou spolupráce při pozastavené, spíše než pozastaveno operačního systému.</span><span class="sxs-lookup"><span data-stu-id="996c5-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996c5-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="996c5-113">Requirements</span></span>  
 <span data-ttu-id="996c5-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996c5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996c5-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="996c5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="996c5-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="996c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996c5-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
