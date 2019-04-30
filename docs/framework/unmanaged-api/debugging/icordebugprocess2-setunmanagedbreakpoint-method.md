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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b374720bd7bdad48222da006b809702de6462a62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948837"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="7f890-102">ICorDebugProcess2::SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="7f890-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="7f890-103">Nastaví nespravované zarážku posunem zadaným nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="7f890-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f890-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f890-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f890-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f890-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="7f890-106">[in] A `CORDB_ADDRESS` objekt, který určuje posun nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="7f890-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="7f890-107">[in] Velikost v bajtech, nástroje `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="7f890-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="7f890-108">[out] Pole, která obsahuje operační kód, který se nahrazuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="7f890-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="7f890-109">[out] Ukazatel na počet bajtů vrácených v `buffer` pole.</span><span class="sxs-lookup"><span data-stu-id="7f890-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f890-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f890-110">Remarks</span></span>  
 <span data-ttu-id="7f890-111">Pokud nativních bitových kopií posun v rámci common language runtime (CLR), zarážka budou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="7f890-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="7f890-112">To umožňuje modulu CLR, aby odesílání out-of-band zarážky, pokud je nastavena zarážka ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="7f890-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f890-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f890-113">Requirements</span></span>  
 <span data-ttu-id="7f890-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f890-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f890-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f890-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f890-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f890-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f890-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f890-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
