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
ms.openlocfilehash: 037e216cb93e3aa6fce28966fc724498024abd52
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789059"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="12b17-102">ICLRDataTarget3::GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="12b17-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="12b17-103">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="12b17-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="12b17-104">Například pro cíl výpisu paměti by to byl ekvivalentem záznamu výjimky předaného prostřednictvím argumentu `ExceptionParam` do funkce [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) v knihovně dbghelp (Windows ladění Help Library).</span><span class="sxs-lookup"><span data-stu-id="12b17-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b17-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12b17-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12b17-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="12b17-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="12b17-107">pro Velikost vstupní vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="12b17-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="12b17-108">Ta musí být rovna `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="12b17-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="12b17-109">mimo Ukazatel na typ `ULONG32`, který přijímá počet bajtů, které jsou ve skutečnosti zapisovány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="12b17-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="12b17-110">mimo Ukazatel na vyrovnávací paměť, která obdrží kopii záznamu výjimky.</span><span class="sxs-lookup"><span data-stu-id="12b17-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="12b17-111">Záznam výjimky je vrácen jako typ [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .</span><span class="sxs-lookup"><span data-stu-id="12b17-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12b17-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12b17-112">Return Value</span></span>  
 <span data-ttu-id="12b17-113">Vrácená hodnota je `S_OK` při úspěchu nebo selhání `HRESULT` kódu při selhání.</span><span class="sxs-lookup"><span data-stu-id="12b17-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="12b17-114">Kódy `HRESULT` mohou zahrnovat, ale nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="12b17-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="12b17-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="12b17-115">Return code</span></span>|<span data-ttu-id="12b17-116">Popis</span><span class="sxs-lookup"><span data-stu-id="12b17-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="12b17-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="12b17-117">Method succeeded.</span></span> <span data-ttu-id="12b17-118">Záznam výjimky byl zkopírován do výstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="12b17-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="12b17-119">K cíli není přidružen žádný záznam výjimky.</span><span class="sxs-lookup"><span data-stu-id="12b17-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="12b17-120">Velikost vstupní vyrovnávací paměti se nerovná `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="12b17-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12b17-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12b17-121">Remarks</span></span>  
 <span data-ttu-id="12b17-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) je struktura definovaná v rámci Windows SDK dbghelp. h a Imagehlp. h.</span><span class="sxs-lookup"><span data-stu-id="12b17-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="12b17-123">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="12b17-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b17-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12b17-124">Requirements</span></span>  
 <span data-ttu-id="12b17-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12b17-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b17-126">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="12b17-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="12b17-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="12b17-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12b17-128">**Verze .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="12b17-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b17-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12b17-129">See also</span></span>

- [<span data-ttu-id="12b17-130">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12b17-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="12b17-131">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="12b17-131">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="12b17-132">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="12b17-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
