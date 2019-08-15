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
ms.openlocfilehash: b667ac16a4bbe6bdab1814b66fb1121b34b2d945
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039573"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="e066e-102">ICLRDataTarget3::GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="e066e-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="e066e-103">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="e066e-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="e066e-104">Například pro cíl výpisu paměti by to byl ekvivalentem záznamu výjimky předaného přes `ExceptionParam` argument do funkce [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) v knihovně dbghelp (ladění v nápovědě systému Windows).</span><span class="sxs-lookup"><span data-stu-id="e066e-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e066e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e066e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e066e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e066e-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="e066e-107">pro Velikost vstupní vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="e066e-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="e066e-108">Toto musí být rovno `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="e066e-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="e066e-109">mimo Ukazatel na `ULONG32` typ, který přijímá počet bajtů, které jsou ve skutečnosti zapisovány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e066e-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e066e-110">mimo Ukazatel na vyrovnávací paměť, která obdrží kopii záznamu výjimky.</span><span class="sxs-lookup"><span data-stu-id="e066e-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="e066e-111">Záznam výjimky je vrácen jako [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) typ.</span><span class="sxs-lookup"><span data-stu-id="e066e-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e066e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e066e-112">Return Value</span></span>  
 <span data-ttu-id="e066e-113">Vrácená hodnota je `S_OK` při úspěchu nebo při selhání kódu chyby `HRESULT` .</span><span class="sxs-lookup"><span data-stu-id="e066e-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="e066e-114">`HRESULT` Kódy mohou zahrnovat, ale nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="e066e-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="e066e-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="e066e-115">Return code</span></span>|<span data-ttu-id="e066e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e066e-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="e066e-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e066e-117">Method succeeded.</span></span> <span data-ttu-id="e066e-118">Záznam výjimky byl zkopírován do výstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e066e-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="e066e-119">K cíli není přidružen žádný záznam výjimky.</span><span class="sxs-lookup"><span data-stu-id="e066e-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="e066e-120">Velikost vstupní vyrovnávací paměti není rovna `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="e066e-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e066e-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e066e-121">Remarks</span></span>  
 <span data-ttu-id="e066e-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) je struktura definovaná v dbghelp. h a Imagehlp. h v Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="e066e-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="e066e-123">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e066e-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e066e-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e066e-124">Requirements</span></span>  
 <span data-ttu-id="e066e-125">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e066e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e066e-126">**Hlaviček** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e066e-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e066e-127">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e066e-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e066e-128">**Verze .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e066e-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e066e-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e066e-129">See also</span></span>

- [<span data-ttu-id="e066e-130">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e066e-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="e066e-131">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="e066e-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="e066e-132">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="e066e-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
