---
title: "IAssemblyName::IsEqual – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.IsEqual
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 454226d45474abea67b944e8437cf53be5c8ed1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="7a7e9-102">IAssemblyName::IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="7a7e9-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="7a7e9-103">Určuje, zda je zadané [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objekt rovná to `IAssemblyName`, podle příznaky zadaný porovnání.</span><span class="sxs-lookup"><span data-stu-id="7a7e9-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a7e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a7e9-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a7e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a7e9-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="7a7e9-106">[v] `IAssemblyName` Objekt, do které chcete porovnat `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="7a7e9-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="7a7e9-107">[v] Bitovou kombinaci [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) hodnoty, které ovlivňují porovnání.</span><span class="sxs-lookup"><span data-stu-id="7a7e9-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a7e9-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a7e9-108">Requirements</span></span>  
 <span data-ttu-id="7a7e9-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a7e9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a7e9-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7a7e9-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7a7e9-111">**NET Framework verze:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a7e9-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a7e9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a7e9-112">See Also</span></span>  
 [<span data-ttu-id="7a7e9-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a7e9-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="7a7e9-114">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="7a7e9-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
