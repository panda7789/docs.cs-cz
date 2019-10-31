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
ms.openlocfilehash: 2358cee1b3a9aa50fb1f0e61d558f164a39aa86c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137365"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="bbab4-102">ICorDebugModule2::SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="bbab4-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="bbab4-103">Nastaví příznaky, které řídí kompilaci JIT (just-in-time) tohoto ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="bbab4-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbab4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbab4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbab4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbab4-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="bbab4-106">pro Bitová kombinace hodnot výčtu [CorDebugJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="bbab4-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbab4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbab4-107">Remarks</span></span>  
 <span data-ttu-id="bbab4-108">Pokud je hodnota `dwFlags` neplatná, metoda `SetJITCompilerFlags` se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="bbab4-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="bbab4-109">Metodu `SetJITCompilerFlags` lze volat pouze v rámci zpětného volání [ICorDebugManagedCallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="bbab4-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="bbab4-110">Pokusí se ji zavolat po doručení `ICorDebugManagedCallback::LoadModule` zpětného volání se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="bbab4-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="bbab4-111">Příkaz Upravit a pokračovat není podporován na platformě 64 a systémy Win9x.</span><span class="sxs-lookup"><span data-stu-id="bbab4-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="bbab4-112">Proto pokud zavoláte metodu `SetJITCompilerFlags` na některé z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastaveným v `dwFlags`, metoda `SetJITCompilerFlags` a všechny metody specifické pro úpravy a pokračování, jako například [ICorDebugModule2:: ApplyChanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="bbab4-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbab4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bbab4-113">Requirements</span></span>  
 <span data-ttu-id="bbab4-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbab4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbab4-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bbab4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbab4-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bbab4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbab4-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbab4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
