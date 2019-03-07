---
title: ICLRDataTarget3::GetExceptionContextRecord – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f5d50ce17b35eb8701fdf115bb5f3b47cba24e2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471235"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="aa51a-102">ICLRDataTarget3::GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="aa51a-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="aa51a-103">Je voláno common language runtime (CLR) data access services k získání záznamu o kontextu souvisejícím s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="aa51a-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="aa51a-104">Například pro cíl s výpisem paměti, jde ekvivalentní k záznamu o kontextu předané prostřednictvím `ExceptionParam` argument [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) funkce ve Windows ladit knihovnu nápovědy (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="aa51a-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa51a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa51a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa51a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa51a-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="aa51a-107">[in] Velikost vstupní vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="aa51a-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="aa51a-108">Toto musí být dostatečně velký, aby kontextového záznamu.</span><span class="sxs-lookup"><span data-stu-id="aa51a-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="aa51a-109">[out] Ukazatel `ULONG32` typ, který přijímá počet bajtů ve skutečnosti zapsat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aa51a-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="aa51a-110">[out] Ukazatel do vyrovnávací paměti, která obdrží kopii kontextového záznamu.</span><span class="sxs-lookup"><span data-stu-id="aa51a-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="aa51a-111">Záznam o výjimce se vrátí jako [kontextu](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) typu.</span><span class="sxs-lookup"><span data-stu-id="aa51a-111">The exception record is returned as a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa51a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa51a-112">Return Value</span></span>  
 <span data-ttu-id="aa51a-113">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kódu při selhání.</span><span class="sxs-lookup"><span data-stu-id="aa51a-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="aa51a-114">`HRESULT` Kódy mohou zahrnovat, avšak nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="aa51a-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="aa51a-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="aa51a-115">Return code</span></span>|<span data-ttu-id="aa51a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="aa51a-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="aa51a-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="aa51a-117">Method succeeded.</span></span> <span data-ttu-id="aa51a-118">Kontextového záznamu byla zkopírována do výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="aa51a-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="aa51a-119">Žádný záznam kontextu je přidružený k cíli.</span><span class="sxs-lookup"><span data-stu-id="aa51a-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="aa51a-120">Velikost vstupní vyrovnávací paměť není dostatečně velký, aby odpovídala kontextového záznamu.</span><span class="sxs-lookup"><span data-stu-id="aa51a-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa51a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa51a-121">Remarks</span></span>  
 <span data-ttu-id="aa51a-122">[KONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) je specifické pro platformu struktuře definované v hlavičkách sada Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="aa51a-122">[CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="aa51a-123">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa51a-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa51a-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa51a-124">Requirements</span></span>  
 <span data-ttu-id="aa51a-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa51a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa51a-126">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="aa51a-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="aa51a-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa51a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa51a-128">**Verze rozhraní .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aa51a-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa51a-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa51a-129">See also</span></span>
- [<span data-ttu-id="aa51a-130">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa51a-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="aa51a-131">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="aa51a-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="aa51a-132">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="aa51a-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
