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
ms.openlocfilehash: 63c92e3f34527f895552f45d43f332f778470b13
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860420"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="a8fdd-102">ICLRDataTarget3::GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="a8fdd-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="a8fdd-103">Voláno pomocí služby Common Language Runtime (CLR) pro získání ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="a8fdd-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8fdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8fdd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8fdd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8fdd-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a8fdd-106">mimo ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="a8fdd-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8fdd-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8fdd-107">Return Value</span></span>  
 <span data-ttu-id="a8fdd-108">Vrácená hodnota je `S_OK` při úspěchu nebo při selhání kódu chyby `HRESULT` .</span><span class="sxs-lookup"><span data-stu-id="a8fdd-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="a8fdd-109">`HRESULT` Kódy mohou zahrnovat, ale nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="a8fdd-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="a8fdd-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="a8fdd-110">Return code</span></span>|<span data-ttu-id="a8fdd-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a8fdd-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="a8fdd-112">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a8fdd-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="a8fdd-113">Pro výjimku se nepovedlo najít platné ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="a8fdd-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8fdd-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8fdd-114">Remarks</span></span>  
 <span data-ttu-id="a8fdd-115">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8fdd-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8fdd-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8fdd-116">Requirements</span></span>  
 <span data-ttu-id="a8fdd-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8fdd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8fdd-118">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a8fdd-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a8fdd-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a8fdd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8fdd-120">**Verze .NET Framework:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a8fdd-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8fdd-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8fdd-121">See also</span></span>

- [<span data-ttu-id="a8fdd-122">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8fdd-122">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="a8fdd-123">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="a8fdd-123">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="a8fdd-124">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="a8fdd-124">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
