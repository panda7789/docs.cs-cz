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
ms.openlocfilehash: 51a4fbe005a8e270b9fe6767ae5173bd027a191b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="40131-102">IAssemblyName::IsEqual – metoda</span><span class="sxs-lookup"><span data-stu-id="40131-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="40131-103">Určuje, zda je zadané [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objekt rovná to `IAssemblyName`, podle příznaky zadaný porovnání.</span><span class="sxs-lookup"><span data-stu-id="40131-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40131-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40131-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40131-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40131-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="40131-106">[v] `IAssemblyName` Objekt, do které chcete porovnat `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="40131-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="40131-107">[v] Bitovou kombinaci [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) hodnoty, které ovlivňují porovnání.</span><span class="sxs-lookup"><span data-stu-id="40131-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40131-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40131-108">Requirements</span></span>  
 <span data-ttu-id="40131-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40131-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40131-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="40131-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="40131-111">**NET Framework verze:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40131-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40131-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="40131-112">See Also</span></span>  
 [<span data-ttu-id="40131-113">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40131-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="40131-114">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="40131-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
