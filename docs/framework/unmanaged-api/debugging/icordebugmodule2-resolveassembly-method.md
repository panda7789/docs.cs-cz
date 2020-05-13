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
ms.openlocfilehash: e64e39d10d20f63430ffe9d2c4df8643e286a677
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210021"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="70fe8-102">ICorDebugModule2::ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="70fe8-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="70fe8-103">Přeloží sestavení, na které odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="70fe8-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="70fe8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70fe8-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="70fe8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70fe8-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="70fe8-106">pro `mdToken`Hodnota, která odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="70fe8-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="70fe8-107">mimo Ukazatel na adresu objektu ICorDebugAssembly, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="70fe8-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="70fe8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70fe8-108">Remarks</span></span>

<span data-ttu-id="70fe8-109">Pokud sestavení již není načteno při `ResolveAssembly` volání, je vrácena hodnota HRESULT CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="70fe8-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="70fe8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70fe8-110">Requirements</span></span>

<span data-ttu-id="70fe8-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70fe8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="70fe8-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70fe8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="70fe8-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="70fe8-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="70fe8-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70fe8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
