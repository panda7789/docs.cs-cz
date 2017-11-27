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
ms.openlocfilehash: 8686e27e63d7363e61bf4c8f1898b71d21fda52b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="d5d7d-102">IInstallReferenceItem::GetReference – metoda</span><span class="sxs-lookup"><span data-stu-id="d5d7d-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="d5d7d-103">Získá odkazy [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktura reprezentována to [iinstallreferenceitem –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="d5d7d-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5d7d-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5d7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5d7d-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="d5d7d-106">[out] Vrácený `FUSION_INSTALL_REFERENCE` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="d5d7d-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d5d7d-107">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d5d7d-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d5d7d-108">`dwFlags`musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="d5d7d-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d5d7d-109">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d5d7d-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d5d7d-110">`pvReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d5d7d-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d7d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5d7d-111">Requirements</span></span>  
 <span data-ttu-id="d5d7d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5d7d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d7d-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d5d7d-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d5d7d-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d7d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d7d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5d7d-115">See Also</span></span>  
 [<span data-ttu-id="d5d7d-116">Iinstallreferenceitem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5d7d-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="d5d7d-117">Fusion_install_reference – struktura</span><span class="sxs-lookup"><span data-stu-id="d5d7d-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
