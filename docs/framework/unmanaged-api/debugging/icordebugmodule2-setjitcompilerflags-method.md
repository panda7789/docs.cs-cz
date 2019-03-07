---
title: ICorDebugModule2::SetJITCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c71ccbc62ea026a55a7e84f6925a78850594a813
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473784"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="203b8-102">ICorDebugModule2::SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="203b8-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="203b8-103">Nastaví příznaky, které řídí tento icordebugmodule2 – kompilace just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="203b8-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="203b8-104">Syntax</span></span>  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="203b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="203b8-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="203b8-106">[in] Bitová kombinace hodnot [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="203b8-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="203b8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="203b8-107">Remarks</span></span>  
 <span data-ttu-id="203b8-108">Pokud `dwFlags` hodnota není platná, `SetJITCompilerFlags` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="203b8-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="203b8-109">`SetJITCompilerFlags` Metodu lze volat pouze v rámci [icordebugmanagedcallback::LoadModule –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) zpětné volání pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="203b8-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="203b8-110">Pokusí se jeho po volání `ICorDebugManagedCallback::LoadModule` byla doručena zpětné volání se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="203b8-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="203b8-111">Upravit a pokračovat není podporována na 64-bit nebo platformách Win9x.</span><span class="sxs-lookup"><span data-stu-id="203b8-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="203b8-112">Proto při volání `SetJITCompilerFlags` metodu na některý z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastavit `dwFlags`, `SetJITCompilerFlags` metoda a všechny metody konkrétní upravit a pokračovat, jako například [icordebugmodule2 –:: Applychanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="203b8-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="203b8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="203b8-113">Requirements</span></span>  
 <span data-ttu-id="203b8-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="203b8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="203b8-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="203b8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="203b8-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="203b8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="203b8-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="203b8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
