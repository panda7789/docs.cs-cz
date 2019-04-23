---
title: ICorDebugDataTarget::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2db073f6bde3ded27f8e1aa41bfcb87e764745f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174964"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="6ed23-102">ICorDebugDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="6ed23-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="6ed23-103">Vrátí kontext aktuálního vlákna pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="6ed23-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed23-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ed23-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="6ed23-106">[in] Identifikátor vlákna, jehož rámci má být načtena.</span><span class="sxs-lookup"><span data-stu-id="6ed23-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="6ed23-107">Identifikátor je definován v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="6ed23-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="6ed23-108">[in] Bitová kombinace příznaků závislého na platformě, které označují, které části kontextu byste si měli přečíst.</span><span class="sxs-lookup"><span data-stu-id="6ed23-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6ed23-109">[in] Velikost `pContext`.</span><span class="sxs-lookup"><span data-stu-id="6ed23-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="6ed23-110">[out] Vyrovnávací paměť, kam se má kontext vlákna uložit.</span><span class="sxs-lookup"><span data-stu-id="6ed23-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed23-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ed23-111">Remarks</span></span>  
 <span data-ttu-id="6ed23-112">Na platformách Windows `pContext` musí být `CONTEXT` strukturu (definované v souboru WinNT.h), který je vhodný pro typ počítače určené [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6ed23-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="6ed23-113">`contextFlags` musí mít stejné hodnoty jako `ContextFlags` pole `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="6ed23-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="6ed23-114">`CONTEXT` Struktura je specifické pro procesor, naleznete v souboru WinNT.h souboru podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="6ed23-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed23-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ed23-115">Requirements</span></span>  
 <span data-ttu-id="6ed23-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed23-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed23-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ed23-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ed23-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ed23-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ed23-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed23-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed23-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ed23-120">See also</span></span>

- [<span data-ttu-id="6ed23-121">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ed23-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="6ed23-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6ed23-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6ed23-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="6ed23-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
