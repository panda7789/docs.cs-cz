---
title: "IInstallReferenceItem::GetReference – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceItem.GetReference
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de21e9b0d224ec417eeb50f8de5c33411d0dadb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="ac061-102">IInstallReferenceItem::GetReference – metoda</span><span class="sxs-lookup"><span data-stu-id="ac061-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="ac061-103">Získá odkazy [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktura reprezentována to [iinstallreferenceitem –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="ac061-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac061-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac061-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac061-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac061-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="ac061-106">[out] Vrácený `FUSION_INSTALL_REFERENCE` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="ac061-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ac061-107">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ac061-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ac061-108">`dwFlags`musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="ac061-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ac061-109">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ac061-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ac061-110">`pvReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ac061-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac061-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac061-111">Requirements</span></span>  
 <span data-ttu-id="ac061-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac061-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac061-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ac061-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ac061-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac061-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac061-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac061-115">See Also</span></span>  
 [<span data-ttu-id="ac061-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac061-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="ac061-117">FUSION_INSTALL_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="ac061-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
