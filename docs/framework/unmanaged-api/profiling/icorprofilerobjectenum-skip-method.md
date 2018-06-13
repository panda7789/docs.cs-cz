---
title: ICorProfilerObjectEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fe35757d895fef3c6267c671f3a91fc50df620a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455677"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="c3a43-102">ICorProfilerObjectEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="c3a43-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="c3a43-103">Posune kurzor tento enumerátoru z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="c3a43-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3a43-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3a43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3a43-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c3a43-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="c3a43-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a43-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3a43-107">Remarks</span></span>  
 <span data-ttu-id="c3a43-108">Nové pozice kurzoru tento výčet je: (aktuální pozici) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="c3a43-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a43-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3a43-109">Requirements</span></span>  
 <span data-ttu-id="c3a43-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a43-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a43-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3a43-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3a43-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3a43-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3a43-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a43-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3a43-114">See Also</span></span>  
 [<span data-ttu-id="c3a43-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3a43-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
