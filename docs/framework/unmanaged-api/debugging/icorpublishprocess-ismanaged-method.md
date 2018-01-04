---
title: "ICorPublishProcess::IsManaged – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21fdb09820acb6357fe1457d2f96c3319b3152a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="cff70-102">ICorPublishProcess::IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="cff70-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="cff70-103">Získá hodnotu, která určuje, jestli proces odkazuje toto [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) se ví, že máte spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cff70-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cff70-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cff70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cff70-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="cff70-106">[out] Ukazatel na logickou hodnotu, která určuje, zda má tento proces spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cff70-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="cff70-107">Hodnota je `true` Pokud proces má spravovaný kód; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="cff70-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cff70-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cff70-108">Remarks</span></span>  
 <span data-ttu-id="cff70-109">Od aktuální verze `ICorPublishProcess` umožňuje přístup pouze k procesy, které mají spravovaného kódu, `IsManaged` vždy vrátí hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="cff70-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff70-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cff70-110">Requirements</span></span>  
 <span data-ttu-id="cff70-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff70-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff70-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="cff70-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cff70-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cff70-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cff70-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff70-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cff70-115">See Also</span></span>  
 [<span data-ttu-id="cff70-116">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cff70-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
