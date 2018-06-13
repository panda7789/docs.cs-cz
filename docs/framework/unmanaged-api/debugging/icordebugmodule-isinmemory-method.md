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
ms.openlocfilehash: 9ae5c16f9f508511e4a15b2eae2c28d68238f1d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415890"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="c75c6-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="c75c6-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="c75c6-103">Získá hodnotu, která určuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="c75c6-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c75c6-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c75c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c75c6-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="c75c6-106">[out] `true` Pokud tento modul pouze v paměti; existuje, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="c75c6-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c75c6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c75c6-107">Remarks</span></span>  
 <span data-ttu-id="c75c6-108">Modul CLR (CLR) podporuje načítání modulů z nezpracovaná datových proudů bajtů.</span><span class="sxs-lookup"><span data-stu-id="c75c6-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="c75c6-109">Tyto moduly se nazývají *moduly v paměti* a nejsou k dispozici na disku.</span><span class="sxs-lookup"><span data-stu-id="c75c6-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c75c6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c75c6-110">Requirements</span></span>  
 <span data-ttu-id="c75c6-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c75c6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c75c6-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c75c6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c75c6-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c75c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c75c6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c75c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75c6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c75c6-115">See Also</span></span>  
    
 
