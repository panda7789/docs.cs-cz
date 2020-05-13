---
title: ICorDebugModule::IsInMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: c5fa55a84ed8907a5072f6099c3bf02cd6d78683
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213124"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="e3d42-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="e3d42-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="e3d42-103">Načte hodnotu, která označuje, jestli tento modul existuje jenom v paměti.</span><span class="sxs-lookup"><span data-stu-id="e3d42-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3d42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3d42-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3d42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3d42-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="e3d42-106">[out] `true` Pokud tento modul existuje pouze v paměti; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="e3d42-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3d42-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3d42-107">Remarks</span></span>  
 <span data-ttu-id="e3d42-108">Modul CLR (Common Language Runtime) podporuje načítání modulů z nezpracovaných datových proudů bajtů.</span><span class="sxs-lookup"><span data-stu-id="e3d42-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="e3d42-109">Tyto moduly se nazývají *moduly v paměti* a neexistují na disku.</span><span class="sxs-lookup"><span data-stu-id="e3d42-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3d42-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3d42-110">Requirements</span></span>  
 <span data-ttu-id="e3d42-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3d42-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3d42-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3d42-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3d42-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e3d42-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3d42-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3d42-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d42-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3d42-115">See also</span></span>
