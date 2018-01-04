---
title: "ICLRDataTarget3::GetExceptionRecord – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e78131eda9d10646a881dbbd4e3f7a4aaf8f607
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="1dd7d-102">ICLRDataTarget3::GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="1dd7d-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="1dd7d-103">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="1dd7d-104">Například pro výpis cíl, by to bylo ekvivalentní předaný prostřednictvím záznam výjimka `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) funkce v knihovně k Windows ladění pomoci (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="1dd7d-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd7d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dd7d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dd7d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dd7d-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="1dd7d-107">[v] Vstupní vyrovnávací paměť velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="1dd7d-108">Toto musí být roven `sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="1dd7d-109">[out] Ukazatel `ULONG32` typ, který obdrží počet bajtů ve skutečnosti zapsat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="1dd7d-110">[out] Ukazatel na vyrovnávací paměť, která obdrží kopii záznam výjimka.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="1dd7d-111">Výjimka záznam se vrátí jako [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) typu.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-111">The exception record is returned as a [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dd7d-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1dd7d-112">Return Value</span></span>  
 <span data-ttu-id="1dd7d-113">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kód při selhání.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="1dd7d-114">`HRESULT` Kódy může zahrnovat, avšak nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="1dd7d-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="1dd7d-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="1dd7d-115">Return code</span></span>|<span data-ttu-id="1dd7d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="1dd7d-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="1dd7d-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-117">Method succeeded.</span></span> <span data-ttu-id="1dd7d-118">Výjimka záznam byl zkopírován do výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="1dd7d-119">Žádný záznam výjimka je přidružený k cíli.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="1dd7d-120">Velikost vstupní vyrovnávací paměť není rovno `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dd7d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1dd7d-121">Remarks</span></span>  
 <span data-ttu-id="1dd7d-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) je struktura definované v dbghelp.h a imagehlp.h ve Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="1dd7d-123">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1dd7d-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd7d-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1dd7d-124">Requirements</span></span>  
 <span data-ttu-id="1dd7d-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd7d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd7d-126">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="1dd7d-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1dd7d-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dd7d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dd7d-128">**Verze rozhraní .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd7d-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd7d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dd7d-129">See Also</span></span>  
 [<span data-ttu-id="1dd7d-130">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1dd7d-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="1dd7d-131">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="1dd7d-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="1dd7d-132">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="1dd7d-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
