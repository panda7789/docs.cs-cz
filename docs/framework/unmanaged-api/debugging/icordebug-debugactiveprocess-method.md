---
title: "ICorDebug::DebugActiveProcess – metoda"
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
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10cb2a5323db67c6f5664e13cb1f97d1a807d20c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="bcbdc-102">ICorDebug::DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="bcbdc-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="bcbdc-103">Připojí ladicí program pro existující proces.</span><span class="sxs-lookup"><span data-stu-id="bcbdc-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcbdc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcbdc-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcbdc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcbdc-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="bcbdc-106">[v] ID procesu, ke kterému má být připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="bcbdc-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="bcbdc-107">[v] Logická hodnota, která je nastavena na `true` Pokud ladicí program by měl chovat jako Win32 ladicí program pro proces a odesílání nespravované zpětná volání; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="bcbdc-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="bcbdc-108">[out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, který byl připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="bcbdc-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcbdc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcbdc-109">Remarks</span></span>  
 <span data-ttu-id="bcbdc-110">Spolupráce ladění není podporována v systémech Windows 9 x a jiný x86 platforem, jako je platformu IA-64 a na základě AMD64 platformy.</span><span class="sxs-lookup"><span data-stu-id="bcbdc-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcbdc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcbdc-111">Requirements</span></span>  
 <span data-ttu-id="bcbdc-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcbdc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcbdc-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcbdc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcbdc-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcbdc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcbdc-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcbdc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcbdc-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcbdc-116">See Also</span></span>  
 [<span data-ttu-id="bcbdc-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcbdc-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
