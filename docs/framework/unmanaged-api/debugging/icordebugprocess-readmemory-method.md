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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218279684304b766a9bf009f5891ac4910254a3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994380"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="03735-102">ICorDebugProcess::ReadMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="03735-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="03735-103">Přečte oblastí paměti pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="03735-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03735-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03735-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03735-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03735-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="03735-106">[in] A `CORDB_ADDRESS` hodnotu, která určuje základní adresu paměti pro čtení.</span><span class="sxs-lookup"><span data-stu-id="03735-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="03735-107">[in] Počet bajtů ke čtení z paměti.</span><span class="sxs-lookup"><span data-stu-id="03735-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="03735-108">[out] Vyrovnávací paměť, která přijímá obsah paměti.</span><span class="sxs-lookup"><span data-stu-id="03735-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="03735-109">[out] Ukazatel na počet bajtů přenesených do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="03735-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03735-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03735-110">Remarks</span></span>  
 <span data-ttu-id="03735-111">`ReadMemory` Metoda je primárně určena pro použití spolupráce laděním ke kontrole oblastí paměti, které se používají v nespravované části laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="03735-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="03735-112">Tato metoda je také možné číst kód Microsoft intermediate language (MSIL) a nativní kód zkompilovaný kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="03735-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="03735-113">Žádné spravované zarážky se odebere z data, která je vrácena v `buffer` parametru.</span><span class="sxs-lookup"><span data-stu-id="03735-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="03735-114">Žádné úpravy pak bude možné pro nativní zarážky nastavil [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="03735-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="03735-115">Neexistující ukládání do mezipaměti z paměti procesu se provádí.</span><span class="sxs-lookup"><span data-stu-id="03735-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03735-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03735-116">Requirements</span></span>  
 <span data-ttu-id="03735-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03735-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03735-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03735-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03735-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03735-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03735-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03735-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
