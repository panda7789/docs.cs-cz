---
title: "ICorDebugILFrame2::RemapFunction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9fed4759576d1b6d2fec1a5e9c1e36019e5944c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="40b7e-102">ICorDebugILFrame2::RemapFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="40b7e-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="40b7e-103">Znovu mapuje upravená funkce zadáním nového posun (MSIL intermediate language) společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="40b7e-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40b7e-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40b7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40b7e-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="40b7e-106">[v] Rámec zásobníku nové MSIL odsazení, kdy má být umístěn ukazatel instrukce</span><span class="sxs-lookup"><span data-stu-id="40b7e-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="40b7e-107">Tato hodnota musí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="40b7e-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="40b7e-108">Je odpovědností volajícího zajistit platnost této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="40b7e-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="40b7e-109">Posun MSIL například není platný, pokud je mimo rozsah funkce.</span><span class="sxs-lookup"><span data-stu-id="40b7e-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40b7e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40b7e-110">Remarks</span></span>  
 <span data-ttu-id="40b7e-111">Pokud bylo upraveno funkce rámečku, můžete volat ladicí program `RemapFunction` metoda do odkládacího souboru v nejnovější verzi funkce rámečku, mohou být provedeny.</span><span class="sxs-lookup"><span data-stu-id="40b7e-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="40b7e-112">Provádění kódu zahájíte na danou MSIL posunu.</span><span class="sxs-lookup"><span data-stu-id="40b7e-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40b7e-113">Volání metody `RemapFunction`, například volání [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), hned zruší platnost všech ladění rozhraní, které se vztahují k generování trasování zásobníku pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="40b7e-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="40b7e-114">Tato rozhraní zahrnují [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, icordebuginternalframe – a ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="40b7e-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="40b7e-115">`RemapFunction` Metodu lze volat pouze v kontextu aktuálního snímku a pouze v jednom z následujících případech:</span><span class="sxs-lookup"><span data-stu-id="40b7e-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
-   <span data-ttu-id="40b7e-116">Po přijetí [icordebugmanagedcallback2::functionremapopportunity –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) zpětné volání, které nebyl ještě dál.</span><span class="sxs-lookup"><span data-stu-id="40b7e-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
-   <span data-ttu-id="40b7e-117">Při provádění kódu je zastavena z důvodu [icordebugmanagedcallback::editandcontinueremap –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) události pro tento snímek.</span><span class="sxs-lookup"><span data-stu-id="40b7e-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40b7e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40b7e-118">Requirements</span></span>  
 <span data-ttu-id="40b7e-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40b7e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40b7e-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40b7e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40b7e-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40b7e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40b7e-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40b7e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
