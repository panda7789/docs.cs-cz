---
title: "ICorDebugProcess::IsOSSuspended – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsOSSuspended
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97c394e3084007227cf157c62a12df3f5cfac8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="1245d-102">ICorDebugProcess::IsOSSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="1245d-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="1245d-103">Získá hodnotu, která určuje zadaný vlákno pozastavila v důsledku ladicí program ukončení tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="1245d-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1245d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1245d-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1245d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1245d-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="1245d-106">[v] ID dotyčném pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1245d-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="1245d-107">[out] Ukazatel na logickou hodnotu, která je `true` Pokud zadané vlákno byl pozastavený; jinak hodnota *`pbSuspended` je `false`.</span><span class="sxs-lookup"><span data-stu-id="1245d-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise *`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1245d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1245d-108">Remarks</span></span>  
 <span data-ttu-id="1245d-109">Pokud v důsledku ladicí program ukončení tohoto procesu se pozastavilo zadaný vlákno, zadaný vlákno Win32 pozastavit počet zvýší o jednu.</span><span class="sxs-lookup"><span data-stu-id="1245d-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="1245d-110">Ladicí program uživatelské rozhraní (UI) chtít provést tyto informace do účtu, pokud se zobrazí operační systém (OS) pozastavit počet vlákno pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="1245d-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="1245d-111">`IsOSSuspended` Metoda má smysl pouze v kontextu nespravované ladění.</span><span class="sxs-lookup"><span data-stu-id="1245d-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="1245d-112">Během spravované ladění vláken jsou spolupráce při pozastavenou spíše než pozastaveno operačního systému.</span><span class="sxs-lookup"><span data-stu-id="1245d-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1245d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1245d-113">Requirements</span></span>  
 <span data-ttu-id="1245d-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1245d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1245d-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1245d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1245d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1245d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1245d-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1245d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
