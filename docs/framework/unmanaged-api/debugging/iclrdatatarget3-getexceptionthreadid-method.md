---
title: ICLRDataTarget3::GetExceptionThreadID – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9b53bb7e34f037f3a165cc8bb59d25ff34ba7da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507145"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="8052c-102">ICLRDataTarget3::GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="8052c-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="8052c-103">Je voláno common language runtime (CLR) data access services k získání ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="8052c-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8052c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8052c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8052c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8052c-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8052c-106">[out] ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="8052c-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8052c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8052c-107">Return Value</span></span>  
 <span data-ttu-id="8052c-108">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kódu při selhání.</span><span class="sxs-lookup"><span data-stu-id="8052c-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="8052c-109">`HRESULT` Kódy mohou zahrnovat, avšak nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="8052c-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="8052c-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="8052c-110">Return code</span></span>|<span data-ttu-id="8052c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8052c-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="8052c-112">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8052c-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="8052c-113">Nelze najít ID vláken pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="8052c-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8052c-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8052c-114">Remarks</span></span>  
 <span data-ttu-id="8052c-115">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8052c-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8052c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8052c-116">Requirements</span></span>  
 <span data-ttu-id="8052c-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8052c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8052c-118">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8052c-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8052c-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8052c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8052c-120">**Verze rozhraní .NET framework:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8052c-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8052c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8052c-121">See also</span></span>
- [<span data-ttu-id="8052c-122">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8052c-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="8052c-123">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="8052c-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="8052c-124">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="8052c-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
