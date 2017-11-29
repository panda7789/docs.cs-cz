---
title: "ICorDebugModule::IsInMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsInMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58f7964faee19f85c83d1b9b1c3e176354ae9588
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="8aa87-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="8aa87-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="8aa87-103">Získá hodnotu, která určuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="8aa87-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aa87-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8aa87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8aa87-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="8aa87-106">[out] `true` Pokud tento modul pouze v paměti; existuje, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="8aa87-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8aa87-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8aa87-107">Remarks</span></span>  
 <span data-ttu-id="8aa87-108">Modul CLR (CLR) podporuje načítání modulů z nezpracovaná datových proudů bajtů.</span><span class="sxs-lookup"><span data-stu-id="8aa87-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="8aa87-109">Tyto moduly se nazývají *moduly v paměti* a nejsou k dispozici na disku.</span><span class="sxs-lookup"><span data-stu-id="8aa87-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aa87-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8aa87-110">Requirements</span></span>  
 <span data-ttu-id="8aa87-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aa87-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aa87-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8aa87-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8aa87-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aa87-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aa87-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aa87-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa87-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8aa87-115">See Also</span></span>  
    
 
