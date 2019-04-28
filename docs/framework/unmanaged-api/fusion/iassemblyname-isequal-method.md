---
title: IAssemblyName::IsEqual – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80402234d9374fa4f16e1f8bb315536a9bdfb2c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697209"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="9941b-102">IAssemblyName::IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="9941b-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="9941b-103">Určuje, zda zadané [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objekt rovná tomuto `IAssemblyName`podle zadané porovnávací příznaky.</span><span class="sxs-lookup"><span data-stu-id="9941b-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9941b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9941b-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9941b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9941b-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="9941b-106">[in] `IAssemblyName` Objekt, na který chcete porovnat `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="9941b-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="9941b-107">[in] Bitová kombinace hodnot [asm_cmp_flags –](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) hodnoty, které ovlivňují porovnání.</span><span class="sxs-lookup"><span data-stu-id="9941b-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9941b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9941b-108">Requirements</span></span>  
 <span data-ttu-id="9941b-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9941b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9941b-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9941b-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9941b-111">**Verze rozhraní .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9941b-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9941b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9941b-112">See also</span></span>

- [<span data-ttu-id="9941b-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9941b-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="9941b-114">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="9941b-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
