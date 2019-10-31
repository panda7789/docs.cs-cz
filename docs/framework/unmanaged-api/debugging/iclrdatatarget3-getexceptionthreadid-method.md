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
ms.openlocfilehash: 5e7fd2f277a9c3d8410020a53d348456ef9deffb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111909"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="ede24-102">ICLRDataTarget3::GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="ede24-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="ede24-103">Voláno pomocí služby Common Language Runtime (CLR) pro získání ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="ede24-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ede24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ede24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ede24-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="ede24-106">mimo ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="ede24-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ede24-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ede24-107">Return Value</span></span>  
 <span data-ttu-id="ede24-108">Vrácená hodnota je `S_OK` při úspěchu nebo selhání `HRESULT` kódu při selhání.</span><span class="sxs-lookup"><span data-stu-id="ede24-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="ede24-109">Kódy `HRESULT` mohou zahrnovat, ale nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="ede24-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="ede24-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="ede24-110">Return code</span></span>|<span data-ttu-id="ede24-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ede24-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="ede24-112">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ede24-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="ede24-113">Pro výjimku se nepovedlo najít platné ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="ede24-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ede24-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ede24-114">Remarks</span></span>  
 <span data-ttu-id="ede24-115">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ede24-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede24-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ede24-116">Requirements</span></span>  
 <span data-ttu-id="ede24-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede24-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede24-118">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ede24-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ede24-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ede24-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ede24-120">**Verze .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ede24-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede24-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ede24-121">See also</span></span>

- [<span data-ttu-id="ede24-122">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede24-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="ede24-123">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="ede24-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="ede24-124">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="ede24-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
