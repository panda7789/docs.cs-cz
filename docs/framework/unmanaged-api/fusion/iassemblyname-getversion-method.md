---
title: IAssemblyName::GetVersion – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5b5f7ce6a4ce8f542b3c49fe4749bfde23ecf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744488"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="b995e-102">IAssemblyName::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="b995e-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="b995e-103">Získá informace o verzi pro sestavení odkazuje situace [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="b995e-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b995e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b995e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b995e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b995e-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="b995e-106">[out] 32 bitů verze.</span><span class="sxs-lookup"><span data-stu-id="b995e-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="b995e-107">[out] Nízká 32 bitů na verzi.</span><span class="sxs-lookup"><span data-stu-id="b995e-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b995e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b995e-108">Requirements</span></span>  
 <span data-ttu-id="b995e-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b995e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b995e-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b995e-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b995e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b995e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b995e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b995e-112">See also</span></span>

- [<span data-ttu-id="b995e-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b995e-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
