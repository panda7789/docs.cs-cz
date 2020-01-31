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
ms.openlocfilehash: aed301fa136ff3d45269c82b46e4cad699074874
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785239"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="03e76-102">ICLRDataTarget3::GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="03e76-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="03e76-103">Volá se službami CLR (Common Language Runtime) k načtení záznamu kontextu přidruženého k cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="03e76-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="03e76-104">Například pro cíl výpisu paměti by to byl ekvivalentem záznamu kontextu předaného pomocí argumentu `ExceptionParam` do funkce [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) v knihovně dbghelp (Windows ladění Help Library).</span><span class="sxs-lookup"><span data-stu-id="03e76-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e76-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03e76-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03e76-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="03e76-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="03e76-107">pro Velikost vstupní vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="03e76-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="03e76-108">Tento postup musí být dostatečně velký, aby mohl být přizpůsoben záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="03e76-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="03e76-109">mimo Ukazatel na typ `ULONG32`, který přijímá počet bajtů, které jsou ve skutečnosti zapisovány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="03e76-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="03e76-110">mimo Ukazatel na vyrovnávací paměť, která obdrží kopii záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="03e76-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="03e76-111">Záznam výjimky je vrácen jako typ [kontextu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="03e76-111">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03e76-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03e76-112">Return Value</span></span>  
 <span data-ttu-id="03e76-113">Vrácená hodnota je `S_OK` při úspěchu nebo selhání `HRESULT` kódu při selhání.</span><span class="sxs-lookup"><span data-stu-id="03e76-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="03e76-114">Kódy `HRESULT` mohou zahrnovat, ale nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="03e76-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="03e76-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="03e76-115">Return code</span></span>|<span data-ttu-id="03e76-116">Popis</span><span class="sxs-lookup"><span data-stu-id="03e76-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="03e76-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="03e76-117">Method succeeded.</span></span> <span data-ttu-id="03e76-118">Záznam kontextu byl zkopírován do výstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="03e76-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="03e76-119">K cíli není přidružen žádný záznam kontextu.</span><span class="sxs-lookup"><span data-stu-id="03e76-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="03e76-120">Velikost vstupní vyrovnávací paměti není dostatečně velká pro přizpůsobení záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="03e76-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03e76-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03e76-121">Remarks</span></span>  
 <span data-ttu-id="03e76-122">[Kontext](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) je struktura specifická pro platformu definovaná v hlavičkách poskytnutých Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="03e76-122">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="03e76-123">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="03e76-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e76-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03e76-124">Requirements</span></span>  
 <span data-ttu-id="03e76-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03e76-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e76-126">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="03e76-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="03e76-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="03e76-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03e76-128">**Verze .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="03e76-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e76-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03e76-129">See also</span></span>

- [<span data-ttu-id="03e76-130">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03e76-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="03e76-131">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="03e76-131">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="03e76-132">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="03e76-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
