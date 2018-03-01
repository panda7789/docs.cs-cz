---
title: "ICLRDataTarget3::GetExceptionThreadID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f8b2e7c764eb5d7694633be7fb095b3d19be6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="07c48-102">ICLRDataTarget3::GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="07c48-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="07c48-103">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup získat ID podprocesu, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="07c48-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07c48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07c48-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07c48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07c48-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="07c48-106">[out] ID podprocesu, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="07c48-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07c48-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="07c48-107">Return Value</span></span>  
 <span data-ttu-id="07c48-108">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kód při selhání.</span><span class="sxs-lookup"><span data-stu-id="07c48-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="07c48-109">`HRESULT` Kódy může zahrnovat, avšak nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="07c48-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="07c48-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="07c48-110">Return code</span></span>|<span data-ttu-id="07c48-111">Popis</span><span class="sxs-lookup"><span data-stu-id="07c48-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="07c48-112">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="07c48-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="07c48-113">Nelze najít ID platný vlákna výjimku.</span><span class="sxs-lookup"><span data-stu-id="07c48-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07c48-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07c48-114">Remarks</span></span>  
 <span data-ttu-id="07c48-115">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="07c48-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07c48-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07c48-116">Requirements</span></span>  
 <span data-ttu-id="07c48-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07c48-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07c48-118">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="07c48-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="07c48-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07c48-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07c48-120">**Verze rozhraní .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07c48-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c48-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="07c48-121">See Also</span></span>  
 [<span data-ttu-id="07c48-122">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07c48-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="07c48-123">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="07c48-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="07c48-124">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="07c48-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
