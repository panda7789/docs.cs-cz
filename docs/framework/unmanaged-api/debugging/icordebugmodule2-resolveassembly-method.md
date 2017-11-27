---
title: "ICorDebugModule2::ResolveAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.ResolveAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37ddb0e8871d9ec5f8eed4f00d81098feafb01de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="a03bf-102">ICorDebugModule2::ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="a03bf-102">ICorDebugModule2::ResolveAssembly Method</span></span>
<span data-ttu-id="a03bf-103">Přeloží sestavení odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="a03bf-103">Resolves the assembly referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a03bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a03bf-104">Syntax</span></span>  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a03bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a03bf-105">Parameters</span></span>  
 `tkAsemblyRef`  
 <span data-ttu-id="a03bf-106">[v] `mdToken` Hodnotu, která odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="a03bf-106">[in] An `mdToken` value that references the assembly.</span></span>  
  
 `ppAssembly`  
 <span data-ttu-id="a03bf-107">[out] Ukazatel na adresu ICorDebugAssembly objekt, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="a03bf-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a03bf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a03bf-108">Remarks</span></span>  
 <span data-ttu-id="a03bf-109">Pokud sestavení dosud není načtený při `ResolveAssembly` nazývá HRESULT je vrácena hodnota CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="a03bf-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a03bf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a03bf-110">Requirements</span></span>  
 <span data-ttu-id="a03bf-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a03bf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a03bf-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a03bf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a03bf-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a03bf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a03bf-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a03bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
