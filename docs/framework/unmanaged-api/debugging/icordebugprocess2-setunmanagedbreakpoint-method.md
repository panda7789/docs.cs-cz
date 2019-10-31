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
ms.openlocfilehash: ffab2762fd86e95c3272ca456039028e0897bc41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137183"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="1c970-102">ICorDebugProcess2::SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="1c970-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="1c970-103">Nastaví nespravovanou zarážku na zadaném posunu nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="1c970-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c970-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c970-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c970-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c970-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1c970-106">pro Objekt `CORDB_ADDRESS`, který určuje posunutí nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="1c970-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="1c970-107">pro Velikost pole `buffer` v bajtech</span><span class="sxs-lookup"><span data-stu-id="1c970-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="1c970-108">mimo Pole, které obsahuje operační kód, který je nahrazen zarážkou.</span><span class="sxs-lookup"><span data-stu-id="1c970-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="1c970-109">mimo Ukazatel na počet bajtů vrácených v poli `buffer`.</span><span class="sxs-lookup"><span data-stu-id="1c970-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c970-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c970-110">Remarks</span></span>  
 <span data-ttu-id="1c970-111">Pokud je posun nativní bitové kopie v rámci modulu CLR (Common Language Runtime), zarážka bude ignorována.</span><span class="sxs-lookup"><span data-stu-id="1c970-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="1c970-112">To umožňuje modulu CLR zabránit odesílání zarážek mimo pásmo, pokud je zarážka nastavena v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="1c970-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c970-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c970-113">Requirements</span></span>  
 <span data-ttu-id="1c970-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c970-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c970-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c970-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c970-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c970-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c970-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c970-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
