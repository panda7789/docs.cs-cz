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
ms.openlocfilehash: 2b99b9c01d014f7b6c02eedde157fa6fdd4e142a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="c52e5-102">IAssemblyName::SetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="c52e5-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="c52e5-103">Nastaví hodnotu vlastnosti odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c52e5-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c52e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c52e5-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c52e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c52e5-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="c52e5-106">[v] Jedinečný identifikátor vlastnosti, jehož hodnota bude nastavena.</span><span class="sxs-lookup"><span data-stu-id="c52e5-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="c52e5-107">[v] Hodnota, pro kterou chcete nastavit vlastnost odkazuje `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="c52e5-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="c52e5-108">[v] Velikost v bajtech z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="c52e5-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c52e5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c52e5-109">Requirements</span></span>  
 <span data-ttu-id="c52e5-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c52e5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c52e5-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c52e5-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c52e5-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c52e5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52e5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c52e5-113">See Also</span></span>  
 [<span data-ttu-id="c52e5-114">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c52e5-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
