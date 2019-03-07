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
ms.openlocfilehash: 7479e8d1eee0c44544b5923d4de66153cb2c3a19
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490330"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="55958-102">IAssemblyName::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="55958-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="55958-103">Získá informace o verzi pro sestavení odkazuje situace [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="55958-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55958-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55958-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55958-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55958-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="55958-106">[out] 32 bitů verze.</span><span class="sxs-lookup"><span data-stu-id="55958-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="55958-107">[out] Nízká 32 bitů na verzi.</span><span class="sxs-lookup"><span data-stu-id="55958-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55958-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55958-108">Requirements</span></span>  
 <span data-ttu-id="55958-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55958-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55958-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="55958-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="55958-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55958-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55958-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55958-112">See also</span></span>
- [<span data-ttu-id="55958-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55958-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
