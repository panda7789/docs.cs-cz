---
title: "IAssemblyName::SetProperty – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.SetProperty
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60ef27021ec3431c90086e0dfbae56bb6e6ccc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="3da30-102">IAssemblyName::SetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="3da30-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="3da30-103">Nastaví hodnotu vlastnosti odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3da30-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3da30-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3da30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3da30-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="3da30-106">[v] Jedinečný identifikátor vlastnosti, jehož hodnota bude nastavena.</span><span class="sxs-lookup"><span data-stu-id="3da30-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="3da30-107">[v] Hodnota, pro kterou chcete nastavit vlastnost odkazuje `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="3da30-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="3da30-108">[v] Velikost v bajtech z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="3da30-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da30-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3da30-109">Requirements</span></span>  
 <span data-ttu-id="3da30-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3da30-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3da30-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3da30-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3da30-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da30-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da30-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3da30-113">See Also</span></span>  
 [<span data-ttu-id="3da30-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3da30-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
