---
title: ICorDebugProcess2::SetUnmanagedBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178639"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="17b0e-102">ICorDebugProcess2::SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="17b0e-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="17b0e-103">Nastaví nespravovanou zarážku na určeném odsazení nativního obrazu.</span><span class="sxs-lookup"><span data-stu-id="17b0e-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17b0e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17b0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17b0e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="17b0e-106">[v] Objekt, `CORDB_ADDRESS` který určuje odsazení nativního obrazu.</span><span class="sxs-lookup"><span data-stu-id="17b0e-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="17b0e-107">[v] Velikost `buffer` pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="17b0e-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="17b0e-108">[out] Pole, které obsahuje operační kód, který je nahrazen zarážkou.</span><span class="sxs-lookup"><span data-stu-id="17b0e-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="17b0e-109">[out] Ukazatel na počet bajtů vrácených `buffer` v poli.</span><span class="sxs-lookup"><span data-stu-id="17b0e-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17b0e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17b0e-110">Remarks</span></span>  
 <span data-ttu-id="17b0e-111">Pokud je posun nativního obrazu v rámci běžného jazykového běhu (CLR), zarážka bude ignorována.</span><span class="sxs-lookup"><span data-stu-id="17b0e-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="17b0e-112">To umožňuje CLR vyhnout se odeslání out-of-band zarážka, při zarážky je nastavenladem.</span><span class="sxs-lookup"><span data-stu-id="17b0e-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17b0e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17b0e-113">Requirements</span></span>  
 <span data-ttu-id="17b0e-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17b0e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17b0e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17b0e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17b0e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17b0e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17b0e-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b0e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
