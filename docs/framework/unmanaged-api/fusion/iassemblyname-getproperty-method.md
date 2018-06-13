---
title: IAssemblyName::GetProperty – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c297c2476cb35fef861cda77f4f6f536fd85557
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428186"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="d1c5b-102">IAssemblyName::GetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="d1c5b-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="d1c5b-103">Získá ukazatel na vlastnost odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d1c5b-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1c5b-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1c5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1c5b-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="d1c5b-106">[v] Jedinečný identifikátor pro požadovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d1c5b-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="d1c5b-107">[out] Data vrácená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d1c5b-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="d1c5b-108">[ve out] Velikost v bajtech z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="d1c5b-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c5b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1c5b-109">Requirements</span></span>  
 <span data-ttu-id="d1c5b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c5b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c5b-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d1c5b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d1c5b-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c5b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c5b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1c5b-113">See Also</span></span>  
 [<span data-ttu-id="d1c5b-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1c5b-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
