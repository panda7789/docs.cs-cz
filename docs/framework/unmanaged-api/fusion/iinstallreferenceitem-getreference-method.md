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
ms.openlocfilehash: 014bd4f2b12c84790065f76a67765aaf35e8b2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131680"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="10265-102">IInstallReferenceItem::GetReference – metoda</span><span class="sxs-lookup"><span data-stu-id="10265-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="10265-103">Získá ukazatel na strukturu [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) reprezentované tímto objektem [IInstallReferenceItem –](iinstallreferenceitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="10265-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10265-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10265-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10265-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10265-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="10265-106">mimo Vrácený ukazatel `FUSION_INSTALL_REFERENCE`.</span><span class="sxs-lookup"><span data-stu-id="10265-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="10265-107">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="10265-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="10265-108">`dwFlags` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="10265-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="10265-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="10265-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="10265-110">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="10265-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10265-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10265-111">Requirements</span></span>  
 <span data-ttu-id="10265-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10265-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10265-113">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="10265-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="10265-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10265-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10265-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10265-115">See also</span></span>

- [<span data-ttu-id="10265-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10265-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="10265-117">FUSION_INSTALL_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="10265-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
