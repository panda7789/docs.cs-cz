---
title: "IAssemblyName::Clone – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.Clone
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 306263bcb27141eadc0943c0045a5f71285436e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="63b7d-102">IAssemblyName::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="63b7d-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="63b7d-103">Vytvoří kopii bez podstruktury tohoto [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="63b7d-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63b7d-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63b7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63b7d-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="63b7d-106">[out] Vrácený kopie `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="63b7d-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63b7d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63b7d-107">Requirements</span></span>  
 <span data-ttu-id="63b7d-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63b7d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63b7d-109">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="63b7d-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="63b7d-110">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b7d-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b7d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="63b7d-111">See Also</span></span>  
 [<span data-ttu-id="63b7d-112">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63b7d-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
