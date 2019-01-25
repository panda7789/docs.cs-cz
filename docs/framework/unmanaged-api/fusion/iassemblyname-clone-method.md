---
title: IAssemblyName::Clone – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550dddea9be711d5821dbc86ab3ca54ab0d967ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598474"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="68d25-102">IAssemblyName::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="68d25-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="68d25-103">Vytvoří Mělkou kopii to [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="68d25-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68d25-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68d25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68d25-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="68d25-106">[out] Vrácené kopie tohoto `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="68d25-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d25-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68d25-107">Requirements</span></span>  
 <span data-ttu-id="68d25-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68d25-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68d25-109">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="68d25-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="68d25-110">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68d25-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d25-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68d25-111">See also</span></span>
- [<span data-ttu-id="68d25-112">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68d25-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
