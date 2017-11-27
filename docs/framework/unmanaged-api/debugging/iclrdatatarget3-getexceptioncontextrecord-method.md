---
title: "ICLRDataTarget3::GetExceptionContextRecord – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c2e645222553f4000b300fa4f010ff81ff44d23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="a42bc-102">ICLRDataTarget3::GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="a42bc-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="a42bc-103">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup k načtení kontextu záznam přidružený tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="a42bc-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="a42bc-104">Například pro výpis cíl, by to bylo ekvivalentní předaný prostřednictvím záznam kontextu `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) funkce v knihovně k Windows ladění pomoci (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="a42bc-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42bc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a42bc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a42bc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a42bc-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="a42bc-107">[v] Vstupní vyrovnávací paměť velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a42bc-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="a42bc-108">Toto musí být dostatečně velký na to, aby dokázala pojmout záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="a42bc-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="a42bc-109">[out] Ukazatel `ULONG32` typ, který obdrží počet bajtů ve skutečnosti zapsat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a42bc-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a42bc-110">[out] Ukazatel na vyrovnávací paměť, která obdrží kopii záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="a42bc-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="a42bc-111">Výjimka záznam se vrátí jako [kontextu](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) typu.</span><span class="sxs-lookup"><span data-stu-id="a42bc-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a42bc-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a42bc-112">Return Value</span></span>  
 <span data-ttu-id="a42bc-113">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kód při selhání.</span><span class="sxs-lookup"><span data-stu-id="a42bc-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="a42bc-114">`HRESULT` Kódy může zahrnovat, avšak nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="a42bc-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="a42bc-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="a42bc-115">Return code</span></span>|<span data-ttu-id="a42bc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a42bc-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="a42bc-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a42bc-117">Method succeeded.</span></span> <span data-ttu-id="a42bc-118">Záznam kontext byl zkopírován do výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="a42bc-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="a42bc-119">Žádný záznam kontextu je přidružený k cíli.</span><span class="sxs-lookup"><span data-stu-id="a42bc-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="a42bc-120">Velikost vstupní vyrovnávací paměť není dostatečně velký na to, aby dokázala pojmout záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="a42bc-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a42bc-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a42bc-121">Remarks</span></span>  
 <span data-ttu-id="a42bc-122">[KONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) je definován v záhlaví poskytované Windows SDK struktura specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="a42bc-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="a42bc-123">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a42bc-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a42bc-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a42bc-124">Requirements</span></span>  
 <span data-ttu-id="a42bc-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a42bc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a42bc-126">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a42bc-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a42bc-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a42bc-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a42bc-128">**Verze rozhraní .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a42bc-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42bc-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="a42bc-129">See Also</span></span>  
 [<span data-ttu-id="a42bc-130">Iclrdatatarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a42bc-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="a42bc-131">Getexceptionrecord – metoda</span><span class="sxs-lookup"><span data-stu-id="a42bc-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="a42bc-132">Metoda GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="a42bc-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
