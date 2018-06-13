---
title: ICorDebugModule2::ResolveAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a6596807b98e6c8b8624b5df18f78dbf8d0711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417775"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="31991-102">ICorDebugModule2::ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="31991-102">ICorDebugModule2::ResolveAssembly Method</span></span>
<span data-ttu-id="31991-103">Přeloží sestavení odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="31991-103">Resolves the assembly referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31991-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31991-104">Syntax</span></span>  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31991-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31991-105">Parameters</span></span>  
 `tkAsemblyRef`  
 <span data-ttu-id="31991-106">[v] `mdToken` Hodnotu, která odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="31991-106">[in] An `mdToken` value that references the assembly.</span></span>  
  
 `ppAssembly`  
 <span data-ttu-id="31991-107">[out] Ukazatel na adresu ICorDebugAssembly objekt, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="31991-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31991-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31991-108">Remarks</span></span>  
 <span data-ttu-id="31991-109">Pokud sestavení dosud není načtený při `ResolveAssembly` nazývá HRESULT je vrácena hodnota CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="31991-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31991-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31991-110">Requirements</span></span>  
 <span data-ttu-id="31991-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31991-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31991-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31991-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31991-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31991-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31991-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31991-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
