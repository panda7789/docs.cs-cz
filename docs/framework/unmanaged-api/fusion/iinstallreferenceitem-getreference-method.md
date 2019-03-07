---
title: IInstallReferenceItem::GetReference – metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85c3fb601cd013eff889e794e71512533f1b12ec
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484677"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="2d63a-102">IInstallReferenceItem::GetReference – metoda</span><span class="sxs-lookup"><span data-stu-id="2d63a-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="2d63a-103">Získá ukazatel [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktura představovaného tímto rozhraním [iinstallreferenceitem –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="2d63a-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d63a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d63a-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d63a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d63a-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="2d63a-106">[out] Vrácený `FUSION_INSTALL_REFERENCE` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2d63a-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2d63a-107">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2d63a-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2d63a-108">`dwFlags` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="2d63a-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2d63a-109">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2d63a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2d63a-110">`pvReserved` musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="2d63a-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d63a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d63a-111">Requirements</span></span>  
 <span data-ttu-id="2d63a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d63a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d63a-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2d63a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2d63a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d63a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d63a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d63a-115">See also</span></span>
- [<span data-ttu-id="2d63a-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d63a-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="2d63a-117">FUSION_INSTALL_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="2d63a-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
