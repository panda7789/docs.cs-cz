---
title: ICorDebugModule::GetAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce1e42d74dc611032d941e833bb8f248a56488b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486249"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="c47f3-102">ICorDebugModule::GetAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="c47f3-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="c47f3-103">Získá obsahující sestavení pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="c47f3-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c47f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c47f3-104">Syntax</span></span>  
  
```  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c47f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c47f3-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="c47f3-106">[out] Ukazatel na objekt icordebugassembly –, který představuje sestavení obsahující tento modul.</span><span class="sxs-lookup"><span data-stu-id="c47f3-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c47f3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c47f3-107">Requirements</span></span>  
 <span data-ttu-id="c47f3-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c47f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c47f3-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c47f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c47f3-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c47f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c47f3-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c47f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
