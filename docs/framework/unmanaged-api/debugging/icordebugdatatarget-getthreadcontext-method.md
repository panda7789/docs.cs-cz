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
ms.openlocfilehash: ab2fbf6bb08a33158ea450f0f19eca50e280d8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412877"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="db8d1-102">ICorDebugDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="db8d1-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="db8d1-103">Vrátí aktuální vlákno kontext pro zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="db8d1-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db8d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db8d1-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db8d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db8d1-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="db8d1-106">[v] Identifikátor vlákno, jehož kontext je mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="db8d1-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="db8d1-107">Identifikátor je definována v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="db8d1-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="db8d1-108">[v] Bitová kombinace příznaky závislé na platformy, které označují, které části kontextu byste si měli přečíst.</span><span class="sxs-lookup"><span data-stu-id="db8d1-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="db8d1-109">[v] Velikost `pContext`.</span><span class="sxs-lookup"><span data-stu-id="db8d1-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="db8d1-110">[out] Vyrovnávací paměť, kde bude uložena kontext přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="db8d1-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db8d1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db8d1-111">Remarks</span></span>  
 <span data-ttu-id="db8d1-112">U platforem Windows `pContext` musí být `CONTEXT` struktury (definovanou v souboru WinNT.h), který je vhodný pro typ počítače určeného [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="db8d1-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="db8d1-113">`contextFlags` musí mít stejné hodnoty jako `ContextFlags` pole z `CONTEXT` struktura.</span><span class="sxs-lookup"><span data-stu-id="db8d1-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="db8d1-114">`CONTEXT` Struktura je specifické pro procesor, naleznete v souboru WinNT.h souboru podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="db8d1-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db8d1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db8d1-115">Requirements</span></span>  
 <span data-ttu-id="db8d1-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db8d1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db8d1-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db8d1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db8d1-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db8d1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db8d1-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db8d1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db8d1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="db8d1-120">See Also</span></span>  
 [<span data-ttu-id="db8d1-121">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db8d1-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="db8d1-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="db8d1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="db8d1-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="db8d1-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
