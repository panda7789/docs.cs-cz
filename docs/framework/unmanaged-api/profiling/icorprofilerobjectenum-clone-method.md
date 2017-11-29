---
title: "ICorProfilerObjectEnum::Clone – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Clone
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e077115863ab3371570463d0bfd9244b69888f9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="e2356-102">ICorProfilerObjectEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="e2356-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="e2356-103">Získá ukazatele rozhraní v kopii [icorprofilerobjectenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e2356-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2356-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2356-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2356-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2356-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e2356-106">[out] Ukazatel na ukazatel rozhraní, která naopak odkazuje na kopii této `ICorProfilerObjectEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e2356-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="e2356-107">Kopie udržuje svou vlastní stav výčtu odděleně od této.</span><span class="sxs-lookup"><span data-stu-id="e2356-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="e2356-108">Pozice kurzoru počáteční vytvoření kopie však bude stejná jako tento enumerátor aktuálním umístěním kurzoru.</span><span class="sxs-lookup"><span data-stu-id="e2356-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2356-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2356-109">Requirements</span></span>  
 <span data-ttu-id="e2356-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2356-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2356-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2356-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2356-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2356-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2356-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2356-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2356-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2356-114">See Also</span></span>  
 [<span data-ttu-id="e2356-115">Icorprofilerobjectenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2356-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
