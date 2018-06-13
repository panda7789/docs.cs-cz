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
ms.openlocfilehash: ee16193c95c9e754f5bff9aeaf37ff74c456891e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428465"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="b42ff-102">IAssemblyName::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="b42ff-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="b42ff-103">Vytvoří kopii bez podstruktury tohoto [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="b42ff-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b42ff-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b42ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b42ff-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b42ff-106">[out] Vrácený kopie `IAssemblyName` objektu.</span><span class="sxs-lookup"><span data-stu-id="b42ff-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42ff-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b42ff-107">Requirements</span></span>  
 <span data-ttu-id="b42ff-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b42ff-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b42ff-109">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b42ff-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b42ff-110">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b42ff-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42ff-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b42ff-111">See Also</span></span>  
 [<span data-ttu-id="b42ff-112">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b42ff-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
