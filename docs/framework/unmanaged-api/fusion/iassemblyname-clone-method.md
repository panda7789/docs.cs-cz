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
ms.openlocfilehash: 2c824874d340aa3d381b3340408021ef1ed7eec6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697445"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="6a421-102">IAssemblyName::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="6a421-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="6a421-103">Vytvoří Mělkou kopii to [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="6a421-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a421-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a421-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a421-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a421-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="6a421-106">[out] Vrácené kopie tohoto `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="6a421-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a421-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a421-107">Requirements</span></span>  
 <span data-ttu-id="6a421-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a421-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a421-109">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6a421-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6a421-110">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a421-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a421-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a421-111">See also</span></span>

- [<span data-ttu-id="6a421-112">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a421-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
