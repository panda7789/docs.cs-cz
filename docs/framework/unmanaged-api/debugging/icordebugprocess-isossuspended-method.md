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
ms.openlocfilehash: 039dc0d9befb038e643abc4e2524c133234f460b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775560"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="a5225-102">ICorDebugProcess::IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="a5225-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="a5225-103">Získá hodnotu určující, zda zadaná vlákna se pozastavilo, v důsledku ukončení tohoto procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="a5225-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5225-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5225-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5225-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5225-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a5225-106">[in] ID vlákna nejistá.</span><span class="sxs-lookup"><span data-stu-id="a5225-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="a5225-107">[out] Ukazatel na logickou hodnotu, která je `true` Pokud vlákna zadaného byl pozastavený, jinak \*`pbSuspended` je `false`.</span><span class="sxs-lookup"><span data-stu-id="a5225-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5225-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5225-108">Remarks</span></span>  
 <span data-ttu-id="a5225-109">Když zadaného vlákna se pozastavilo, v důsledku ukončení tohoto procesu ladicího programu, zadané vlákno Win32 pozastavit počet se zvýší o jedna.</span><span class="sxs-lookup"><span data-stu-id="a5225-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="a5225-110">Uživatelské rozhraní (UI) ladicí program může být vhodné vzít v úvahu tyto informace pokud zobrazí operační systém (OS) pozastavit počet vláken pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="a5225-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="a5225-111">`IsOSSuspended` Metoda má smysl pouze v kontextu ladění nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a5225-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="a5225-112">Při ladění spravovaných vláken jsou spolupráce při pozastavené, spíše než pozastaveno operačního systému.</span><span class="sxs-lookup"><span data-stu-id="a5225-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5225-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5225-113">Requirements</span></span>  
 <span data-ttu-id="a5225-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5225-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5225-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5225-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5225-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5225-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5225-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5225-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
