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
ms.openlocfilehash: f73919634ba15dfd16694676d1389875fc2d79bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210186"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="7d90d-102">ICorDebugModule2::SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="7d90d-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="7d90d-103">Nastaví příznaky, které řídí kompilaci JIT (just-in-time) tohoto ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="7d90d-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d90d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d90d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d90d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d90d-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="7d90d-106">pro Bitová kombinace hodnot výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7d90d-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d90d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d90d-107">Remarks</span></span>  
 <span data-ttu-id="7d90d-108">Pokud `dwFlags` je hodnota neplatná, `SetJITCompilerFlags` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7d90d-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="7d90d-109">`SetJITCompilerFlags`Metodu lze volat pouze v rámci zpětného volání [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="7d90d-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="7d90d-110">Pokusy o jeho volání po `ICorDebugManagedCallback::LoadModule` doručení zpětného volání se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7d90d-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="7d90d-111">Příkaz Upravit a pokračovat není podporován na platformě 64 a systémy Win9x.</span><span class="sxs-lookup"><span data-stu-id="7d90d-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="7d90d-112">Proto pokud voláte `SetJITCompilerFlags` metodu na některé z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastaveným v `dwFlags` , `SetJITCompilerFlags` Metoda a všechny metody specifické pro příkaz Upravit a pokračovat, například [ICorDebugModule2:: ApplyChanges –](icordebugmodule2-applychanges-method.md), selžou.</span><span class="sxs-lookup"><span data-stu-id="7d90d-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d90d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d90d-113">Requirements</span></span>  
 <span data-ttu-id="7d90d-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d90d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d90d-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d90d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d90d-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d90d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d90d-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d90d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
