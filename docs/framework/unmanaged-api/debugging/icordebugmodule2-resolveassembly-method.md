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
ms.openlocfilehash: fd899422287d34407778f67e5b4dfd2f33ffd00c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359689"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="1140c-102">ICorDebugModule2::ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="1140c-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="1140c-103">Přeloží sestavení odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="1140c-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="1140c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1140c-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="1140c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1140c-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="1140c-106">[in] `mdToken` Hodnotu, která odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="1140c-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="1140c-107">[out] Ukazatel na adresu icordebugassembly – objekt, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="1140c-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="1140c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1140c-108">Remarks</span></span>

<span data-ttu-id="1140c-109">Pokud sestavení ještě není zaveden při `ResolveAssembly` nazývá HRESULT je vrácena hodnota CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="1140c-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="1140c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1140c-110">Requirements</span></span>

<span data-ttu-id="1140c-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1140c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="1140c-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1140c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="1140c-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1140c-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1140c-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1140c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
