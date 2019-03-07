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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f057896d9dd65a850c0b07e4084bc263e804d20
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497363"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="2335c-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="2335c-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="2335c-103">Získá hodnotu, která označuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="2335c-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2335c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2335c-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2335c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2335c-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="2335c-106">[out] `true` Pokud tento modul existuje pouze v paměti; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2335c-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2335c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2335c-107">Remarks</span></span>  
 <span data-ttu-id="2335c-108">Modul CLR (CLR) podporuje načítání modulů z nezpracované datové proudy bajtů.</span><span class="sxs-lookup"><span data-stu-id="2335c-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="2335c-109">Tyto moduly se nazývají *moduly v paměti* a neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="2335c-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2335c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2335c-110">Requirements</span></span>  
 <span data-ttu-id="2335c-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2335c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2335c-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2335c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2335c-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2335c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2335c-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2335c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2335c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2335c-115">See also</span></span>


