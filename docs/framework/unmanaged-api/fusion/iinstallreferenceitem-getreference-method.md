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
ms.openlocfilehash: 9395fcc6d896114c25770edbc17761323285099f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796391"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="567b9-102">IInstallReferenceItem::GetReference – metoda</span><span class="sxs-lookup"><span data-stu-id="567b9-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="567b9-103">Získá ukazatel na strukturu [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) reprezentované tímto objektem [IInstallReferenceItem –](iinstallreferenceitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="567b9-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="567b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="567b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="567b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="567b9-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="567b9-106">mimo Vrácený `FUSION_INSTALL_REFERENCE` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="567b9-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="567b9-107">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="567b9-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="567b9-108">`dwFlags`musí mít hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="567b9-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="567b9-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="567b9-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="567b9-110">`pvReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="567b9-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="567b9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="567b9-111">Requirements</span></span>  
 <span data-ttu-id="567b9-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="567b9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="567b9-113">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="567b9-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="567b9-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="567b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="567b9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="567b9-115">See also</span></span>

- [<span data-ttu-id="567b9-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="567b9-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="567b9-117">FUSION_INSTALL_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="567b9-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
