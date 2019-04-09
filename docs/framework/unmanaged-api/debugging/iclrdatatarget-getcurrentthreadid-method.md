---
title: ICLRDataTarget::GetCurrentThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9687f6139d67a2387091367c2c72167e03be4eee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080654"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="f6b0d-102">ICLRDataTarget::GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="f6b0d-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="f6b0d-103">Získá identifikátor operačního systému pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f6b0d-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6b0d-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6b0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6b0d-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="f6b0d-106">[out] Ukazatel na operační systém identifikátor aktuálního vlákna pro cílový proces.</span><span class="sxs-lookup"><span data-stu-id="f6b0d-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6b0d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6b0d-107">Remarks</span></span>  
 <span data-ttu-id="f6b0d-108">Pokud není žádná aktuální vlákno pro cílový proces `GetCurrentThreadID` metoda může selhat.</span><span class="sxs-lookup"><span data-stu-id="f6b0d-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6b0d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6b0d-109">Requirements</span></span>  
 <span data-ttu-id="f6b0d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6b0d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6b0d-111">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f6b0d-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f6b0d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6b0d-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f6b0d-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f6b0d-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6b0d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6b0d-114">See also</span></span>

- [<span data-ttu-id="f6b0d-115">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6b0d-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
