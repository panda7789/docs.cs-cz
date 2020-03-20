---
title: ICorDebugProcess::ReadMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178654"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="e49e4-102">ICorDebugProcess::ReadMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="e49e4-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="e49e4-103">Přečte zadanou oblast paměti pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="e49e4-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e49e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e49e4-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e49e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e49e4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e49e4-106">[v] Hodnota, `CORDB_ADDRESS` která určuje základní adresu paměti, která má být přečtena.</span><span class="sxs-lookup"><span data-stu-id="e49e4-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="e49e4-107">[v] Počet bajtů, které mají být přečteny z paměti.</span><span class="sxs-lookup"><span data-stu-id="e49e4-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e49e4-108">[out] Vyrovnávací paměť, která přijímá obsah paměti.</span><span class="sxs-lookup"><span data-stu-id="e49e4-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="e49e4-109">[out] Ukazatel na počet bajtů přenesených do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e49e4-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e49e4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e49e4-110">Remarks</span></span>  
 <span data-ttu-id="e49e4-111">Metoda `ReadMemory` je primárně určena pro použití interop ladění ke kontrole oblastí paměti, které jsou používány nespravované části ladicí.</span><span class="sxs-lookup"><span data-stu-id="e49e4-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="e49e4-112">Tuto metodu lze také ke čtení kódu zprostředkujícíjazyk společnosti Microsoft (MSIL) a nativní jit kompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e49e4-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="e49e4-113">Všechny spravované zarážky budou odebrány z dat, která je vrácena v parametru. `buffer`</span><span class="sxs-lookup"><span data-stu-id="e49e4-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="e49e4-114">Nebudou provedeny žádné úpravy pro nativní zarážky nastavené [iCorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="e49e4-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="e49e4-115">Není prováděno ukládání paměti procesu do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e49e4-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e49e4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e49e4-116">Requirements</span></span>  
 <span data-ttu-id="e49e4-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e49e4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e49e4-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e49e4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e49e4-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e49e4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e49e4-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e49e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
