---
title: ICorDebug::DebugActiveProcess – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84137e7163101f7eaa54a45df0fbaa4e7bcf70fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404583"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="1eb7d-102">ICorDebug::DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="1eb7d-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="1eb7d-103">Připojí ladicí program pro existující proces.</span><span class="sxs-lookup"><span data-stu-id="1eb7d-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eb7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1eb7d-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1eb7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1eb7d-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="1eb7d-106">[v] ID procesu, ke kterému má být připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="1eb7d-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="1eb7d-107">[v] Logická hodnota, která je nastavena na `true` Pokud ladicí program by měl chovat jako Win32 ladicí program pro proces a odesílání nespravované zpětná volání; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="1eb7d-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="1eb7d-108">[out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, který byl připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="1eb7d-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1eb7d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1eb7d-109">Remarks</span></span>  
 <span data-ttu-id="1eb7d-110">Spolupráce ladění není podporována v systémech Windows 9 x a jiný x86 platforem, jako je platformu IA-64 a na základě AMD64 platformy.</span><span class="sxs-lookup"><span data-stu-id="1eb7d-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eb7d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1eb7d-111">Requirements</span></span>  
 <span data-ttu-id="1eb7d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eb7d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eb7d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1eb7d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1eb7d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1eb7d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eb7d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eb7d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb7d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1eb7d-116">See Also</span></span>  
 [<span data-ttu-id="1eb7d-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1eb7d-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
