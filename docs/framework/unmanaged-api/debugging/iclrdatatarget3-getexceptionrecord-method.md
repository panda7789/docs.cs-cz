---
title: ICLRDataTarget3::GetExceptionRecord – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19e348f63af181b80b0924b0f2d3be156703595d
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065918"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="712e4-102">ICLRDataTarget3::GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="712e4-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="712e4-103">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="712e4-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="712e4-104">Například pro cíl s výpisem paměti, jde ekvivalentní k záznamu o výjimce předaný prostřednictvím `ExceptionParam` argument [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) funkce ve Windows ladit knihovnu nápovědy (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="712e4-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712e4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="712e4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="712e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="712e4-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="712e4-107">[in] Velikost vstupní vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="712e4-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="712e4-108">Toto musí být rovna `sizeof(` [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="712e4-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="712e4-109">[out] Ukazatel `ULONG32` typ, který přijímá počet bajtů ve skutečnosti zapsat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="712e4-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="712e4-110">[out] Ukazatel do vyrovnávací paměti, která obdrží kopii záznam o výjimce.</span><span class="sxs-lookup"><span data-stu-id="712e4-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="712e4-111">Záznam o výjimce se vrátí jako [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) typu.</span><span class="sxs-lookup"><span data-stu-id="712e4-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="712e4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="712e4-112">Return Value</span></span>  
 <span data-ttu-id="712e4-113">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kódu při selhání.</span><span class="sxs-lookup"><span data-stu-id="712e4-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="712e4-114">`HRESULT` Kódy mohou zahrnovat, avšak nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="712e4-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="712e4-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="712e4-115">Return code</span></span>|<span data-ttu-id="712e4-116">Popis</span><span class="sxs-lookup"><span data-stu-id="712e4-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="712e4-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712e4-117">Method succeeded.</span></span> <span data-ttu-id="712e4-118">Záznam o výjimce byl zkopírován do výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="712e4-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="712e4-119">Žádný záznam o výjimce je přidružený k cíli.</span><span class="sxs-lookup"><span data-stu-id="712e4-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="712e4-120">Velikost vstupní vyrovnávací paměť není roven `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="712e4-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="712e4-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="712e4-121">Remarks</span></span>  
 <span data-ttu-id="712e4-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) je struktura definované v dbghelp.h a imagehlp.h v sadě Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="712e4-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="712e4-123">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="712e4-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="712e4-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="712e4-124">Requirements</span></span>  
 <span data-ttu-id="712e4-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="712e4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712e4-126">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="712e4-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="712e4-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="712e4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="712e4-128">**Verze rozhraní .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="712e4-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712e4-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="712e4-129">See also</span></span>
- [<span data-ttu-id="712e4-130">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="712e4-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="712e4-131">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="712e4-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="712e4-132">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="712e4-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
