---
title: IInstallReferenceEnum::GetNextInstallReferenceItem – metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c23494f8c0a977624b899f01e843ba3545a22fbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501640"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="63c5f-102">IInstallReferenceEnum::GetNextInstallReferenceItem – metoda</span><span class="sxs-lookup"><span data-stu-id="63c5f-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="63c5f-103">Získá ukazatel na další [iinstallreferenceitem –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objektů obsažených v tomto [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="63c5f-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63c5f-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63c5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63c5f-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="63c5f-106">[out] Vrácený `IInstallReferenceItem` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="63c5f-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="63c5f-107">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="63c5f-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="63c5f-108">`dwFlags` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="63c5f-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="63c5f-109">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="63c5f-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="63c5f-110">`pvReserved` musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="63c5f-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c5f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63c5f-111">Requirements</span></span>  
 <span data-ttu-id="63c5f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c5f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c5f-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="63c5f-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="63c5f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c5f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c5f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63c5f-115">See also</span></span>
- [<span data-ttu-id="63c5f-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63c5f-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="63c5f-117">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63c5f-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
