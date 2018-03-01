---
title: "ICorDebugDataTarget::GetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44543ca3546827b38643cab0e047032a96be9ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="b170b-102">ICorDebugDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="b170b-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="b170b-103">Vrátí aktuální vlákno kontext pro zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="b170b-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b170b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b170b-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b170b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b170b-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="b170b-106">[v] Identifikátor vlákno, jehož kontext je mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="b170b-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="b170b-107">Identifikátor je definována v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="b170b-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="b170b-108">[v] Bitová kombinace příznaky závislé na platformy, které označují, které části kontextu byste si měli přečíst.</span><span class="sxs-lookup"><span data-stu-id="b170b-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b170b-109">[v] Velikost `pContext`.</span><span class="sxs-lookup"><span data-stu-id="b170b-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="b170b-110">[out] Vyrovnávací paměť, kde bude uložena kontext přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="b170b-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b170b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b170b-111">Remarks</span></span>  
 <span data-ttu-id="b170b-112">U platforem Windows `pContext` musí být `CONTEXT` struktury (definovanou v souboru WinNT.h), který je vhodný pro typ počítače určeného [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="b170b-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="b170b-113">`contextFlags`musí mít stejné hodnoty jako `ContextFlags` pole z `CONTEXT` struktura.</span><span class="sxs-lookup"><span data-stu-id="b170b-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="b170b-114">`CONTEXT` Struktura je specifické pro procesor, naleznete v souboru WinNT.h souboru podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="b170b-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b170b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b170b-115">Requirements</span></span>  
 <span data-ttu-id="b170b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b170b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b170b-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b170b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b170b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b170b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b170b-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b170b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b170b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b170b-120">See Also</span></span>  
 [<span data-ttu-id="b170b-121">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b170b-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="b170b-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b170b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b170b-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="b170b-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
