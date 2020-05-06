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
ms.openlocfilehash: 3e73d0fc48dcfeafb3fe2f23ec07cdc04a561a9e
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860445"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="696f9-102">ICLRDataTarget3::GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="696f9-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="696f9-103">Volá se službami CLR (Common Language Runtime) k načtení záznamu kontextu přidruženého k cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="696f9-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="696f9-104">Například pro cíl výpisu paměti by to byl ekvivalentem záznamu kontextu předaného přes `ExceptionParam` argument do funkce [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) v knihovně dbghelp (ladění v nápovědě systému Windows).</span><span class="sxs-lookup"><span data-stu-id="696f9-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696f9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="696f9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="696f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="696f9-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="696f9-107">pro Velikost vstupní vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="696f9-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="696f9-108">Tento postup musí být dostatečně velký, aby mohl být přizpůsoben záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="696f9-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="696f9-109">mimo Ukazatel na `ULONG32` typ, který přijímá počet bajtů, které jsou ve skutečnosti zapisovány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="696f9-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="696f9-110">mimo Ukazatel na vyrovnávací paměť, která obdrží kopii záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="696f9-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="696f9-111">Záznam výjimky je vrácen jako typ [kontextu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="696f9-111">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="696f9-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="696f9-112">Return Value</span></span>  
 <span data-ttu-id="696f9-113">Vrácená hodnota je `S_OK` při úspěchu nebo při selhání kódu chyby `HRESULT` .</span><span class="sxs-lookup"><span data-stu-id="696f9-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="696f9-114">`HRESULT` Kódy mohou zahrnovat, ale nejsou omezeny na následující:</span><span class="sxs-lookup"><span data-stu-id="696f9-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="696f9-115">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="696f9-115">Return code</span></span>|<span data-ttu-id="696f9-116">Popis</span><span class="sxs-lookup"><span data-stu-id="696f9-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="696f9-117">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="696f9-117">Method succeeded.</span></span> <span data-ttu-id="696f9-118">Záznam kontextu byl zkopírován do výstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="696f9-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="696f9-119">K cíli není přidružen žádný záznam kontextu.</span><span class="sxs-lookup"><span data-stu-id="696f9-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="696f9-120">Velikost vstupní vyrovnávací paměti není dostatečně velká pro přizpůsobení záznamu kontextu.</span><span class="sxs-lookup"><span data-stu-id="696f9-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="696f9-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="696f9-121">Remarks</span></span>  
 <span data-ttu-id="696f9-122">[Kontext](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) je struktura specifická pro platformu definovaná v hlavičkách poskytnutých Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="696f9-122">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="696f9-123">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="696f9-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696f9-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="696f9-124">Requirements</span></span>  
 <span data-ttu-id="696f9-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="696f9-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696f9-126">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="696f9-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="696f9-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="696f9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="696f9-128">**Verze .NET Framework:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="696f9-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696f9-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="696f9-129">See also</span></span>

- [<span data-ttu-id="696f9-130">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="696f9-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="696f9-131">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="696f9-131">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="696f9-132">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="696f9-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
