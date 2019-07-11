---
title: IAssemblyName::SetProperty – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40953d03904e3268770c8a1b6e212873ec66d2dd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761845"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="4d1bb-102">IAssemblyName::SetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="4d1bb-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="4d1bb-103">Nastaví hodnotu vlastnosti odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4d1bb-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d1bb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d1bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d1bb-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="4d1bb-106">[in] Jedinečný identifikátor vlastnosti, jehož hodnota bude nastavena.</span><span class="sxs-lookup"><span data-stu-id="4d1bb-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="4d1bb-107">[in] Hodnota, na kterou odkazuje vlastnost `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="4d1bb-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="4d1bb-108">[in] Velikost v bajtech, z `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="4d1bb-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d1bb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d1bb-109">Requirements</span></span>  
 <span data-ttu-id="4d1bb-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d1bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d1bb-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4d1bb-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4d1bb-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d1bb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1bb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d1bb-113">See also</span></span>

- [<span data-ttu-id="4d1bb-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d1bb-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
