---
title: "ICorProfilerObjectEnum::Skip – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84960af6e128f3a6aa9e3b45187e282ac7228e0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="8e8d2-102">ICorProfilerObjectEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="8e8d2-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="8e8d2-103">Posune kurzor tento enumerátoru z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="8e8d2-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e8d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e8d2-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e8d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e8d2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8e8d2-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="8e8d2-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e8d2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e8d2-107">Remarks</span></span>  
 <span data-ttu-id="8e8d2-108">Nové pozice kurzoru tento výčet je: (aktuální pozici) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="8e8d2-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e8d2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e8d2-109">Requirements</span></span>  
 <span data-ttu-id="8e8d2-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e8d2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e8d2-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e8d2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e8d2-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e8d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e8d2-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e8d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e8d2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e8d2-114">See Also</span></span>  
 [<span data-ttu-id="8e8d2-115">Icorprofilerobjectenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e8d2-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
