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
ms.openlocfilehash: 8ce2203456fdd3c749d3477b0c400c00e4e2cd04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="7b358-102">IAssemblyName::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="7b358-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="7b358-103">Vytvoří kopii bez podstruktury tohoto [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="7b358-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b358-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b358-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b358-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b358-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="7b358-106">[out] Vrácený kopie `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="7b358-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b358-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b358-107">Requirements</span></span>  
 <span data-ttu-id="7b358-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b358-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b358-109">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7b358-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7b358-110">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b358-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b358-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b358-111">See Also</span></span>  
 [<span data-ttu-id="7b358-112">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b358-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
