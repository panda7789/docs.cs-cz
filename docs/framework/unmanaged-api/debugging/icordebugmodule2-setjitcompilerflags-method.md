---
title: "ICorDebugModule2::SetJITCompilerFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42eea356214fedb22a2f60842f6007f3eb6a0e2a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="83bb6-102">ICorDebugModule2::SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="83bb6-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="83bb6-103">Nastaví příznaky, které řídí tento ICorDebugModule2 kompilace v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="83bb6-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83bb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83bb6-104">Syntax</span></span>  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83bb6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83bb6-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="83bb6-106">[v] Bitové kombinace [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="83bb6-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83bb6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83bb6-107">Remarks</span></span>  
 <span data-ttu-id="83bb6-108">Pokud `dwFlags` hodnota je neplatná, `SetJITCompilerFlags` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="83bb6-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="83bb6-109">`SetJITCompilerFlags` Metodu lze volat pouze z uvnitř [icordebugmanagedcallback::LoadModule –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) zpětného volání pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="83bb6-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="83bb6-110">Pokusí se ji po volání `ICorDebugManagedCallback::LoadModule` zpětného volání byla doručena se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="83bb6-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="83bb6-111">Upravit a pokračovat není podporována na 64-bit nebo systémy Windows 9 x platformy.</span><span class="sxs-lookup"><span data-stu-id="83bb6-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="83bb6-112">Proto při volání `SetJITCompilerFlags` metoda na některou z těchto dvou platforem s příznakem CORDEBUG_JIT_ENABLE_ENC nastaveným `dwFlags`, `SetJITCompilerFlags` metoda a všechny metody, které jsou specifické pro upravit a pokračovat, jako například [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="83bb6-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83bb6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83bb6-113">Requirements</span></span>  
 <span data-ttu-id="83bb6-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83bb6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83bb6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83bb6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83bb6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83bb6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83bb6-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83bb6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
