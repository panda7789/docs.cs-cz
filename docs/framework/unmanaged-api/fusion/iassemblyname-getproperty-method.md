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
ms.openlocfilehash: 9af0773c2ef066c103f823e4d28c0fd6e9eadc24
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086556"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="6d4df-102">IAssemblyName::GetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="6d4df-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="6d4df-103">Získá ukazatel na vlastnosti odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6d4df-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d4df-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d4df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d4df-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="6d4df-106">[in] Jedinečný identifikátor pro požadovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6d4df-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="6d4df-107">[out] Data vrácená vlastností.</span><span class="sxs-lookup"><span data-stu-id="6d4df-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="6d4df-108">[out v] Velikost v bajtech, z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="6d4df-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d4df-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d4df-109">Requirements</span></span>  
 <span data-ttu-id="6d4df-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d4df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d4df-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6d4df-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="6d4df-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6d4df-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d4df-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d4df-113">See also</span></span>

- [<span data-ttu-id="6d4df-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d4df-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
