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
ms.openlocfilehash: 93a85f2fd0f2095ce22bd69a3251d7950fcdb529
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57464591"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="33576-102">IAssemblyName::GetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="33576-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="33576-103">Získá ukazatel na vlastnosti odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="33576-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33576-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33576-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33576-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33576-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="33576-106">[in] Jedinečný identifikátor pro požadovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="33576-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="33576-107">[out] Data vrácená vlastností.</span><span class="sxs-lookup"><span data-stu-id="33576-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="33576-108">[out v] Velikost v bajtech, z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="33576-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33576-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33576-109">Requirements</span></span>  
 <span data-ttu-id="33576-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33576-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33576-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="33576-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="33576-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33576-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33576-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33576-113">See also</span></span>
- [<span data-ttu-id="33576-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33576-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
