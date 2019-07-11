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
ms.openlocfilehash: fe94203d315c32b62a191adf294a9c1310fe28e0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738259"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="381a9-102">ICorDebug::DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="381a9-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="381a9-103">Připojí ladicí program k existujícímu procesu.</span><span class="sxs-lookup"><span data-stu-id="381a9-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="381a9-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="381a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="381a9-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="381a9-106">[in] ID procesu, ke kterému je ladicí program připojit.</span><span class="sxs-lookup"><span data-stu-id="381a9-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="381a9-107">[in] Logická hodnota, která je nastavena na `true` Pokud ladicí program by měl chovat jako ladicí program systému Win32 pro proces a odeslání nespravované zpětná volání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="381a9-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="381a9-108">[out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, ke kterému je připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="381a9-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="381a9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="381a9-109">Remarks</span></span>  
 <span data-ttu-id="381a9-110">Definiční ladění není podporováno na platformách Win9x a x x86, jako jsou založené na IA-64 a AMD64 podle platformy.</span><span class="sxs-lookup"><span data-stu-id="381a9-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="381a9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="381a9-111">Requirements</span></span>  
 <span data-ttu-id="381a9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="381a9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="381a9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="381a9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="381a9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="381a9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="381a9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="381a9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381a9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="381a9-116">See also</span></span>

- [<span data-ttu-id="381a9-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="381a9-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
