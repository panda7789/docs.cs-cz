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
ms.openlocfilehash: ccd2350589126109ff11da439a8b83abfc4b91fa
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210472"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="5e083-102">ICorDebugProcess::ReadMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="5e083-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="5e083-103">Přečte zadanou oblast paměti pro tento proces.</span><span class="sxs-lookup"><span data-stu-id="5e083-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e083-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e083-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e083-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e083-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5e083-106">pro `CORDB_ADDRESS`Hodnota, která určuje základní adresu paměti, která se má číst.</span><span class="sxs-lookup"><span data-stu-id="5e083-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="5e083-107">pro Počet bajtů, které mají být načteny z paměti.</span><span class="sxs-lookup"><span data-stu-id="5e083-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="5e083-108">mimo Vyrovnávací paměť, která přijímá obsah paměti.</span><span class="sxs-lookup"><span data-stu-id="5e083-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="5e083-109">mimo Ukazatel na počet bajtů přenesených do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5e083-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e083-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e083-110">Remarks</span></span>  
 <span data-ttu-id="5e083-111">`ReadMemory`Metoda je primárně určena pro účely ladění v oblasti paměti, které jsou používány nespravovanou částí laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="5e083-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="5e083-112">Tuto metodu lze také použít ke čtení kódu jazyka MSIL (Microsoft Intermediate Language) a nativního kódu kompilovaného JIT.</span><span class="sxs-lookup"><span data-stu-id="5e083-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="5e083-113">Všechny spravované zarážky budou odebrány z dat vrácených v `buffer` parametru.</span><span class="sxs-lookup"><span data-stu-id="5e083-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="5e083-114">Pro nativní zarážky nastavené pomocí [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md)se nevytvoří žádné úpravy.</span><span class="sxs-lookup"><span data-stu-id="5e083-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="5e083-115">Není provedeno ukládání paměti procesu do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5e083-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e083-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e083-116">Requirements</span></span>  
 <span data-ttu-id="5e083-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e083-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e083-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e083-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e083-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e083-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e083-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e083-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
