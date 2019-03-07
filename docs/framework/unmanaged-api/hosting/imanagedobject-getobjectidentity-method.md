---
title: IManagedObject::GetObjectIdentity – metoda
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d825a0c67f88e1f37023feb96a217b115653056
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496934"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="8fe31-102">IManagedObject::GetObjectIdentity – metoda</span><span class="sxs-lookup"><span data-stu-id="8fe31-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="8fe31-103">Získá identitu tohoto spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="8fe31-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fe31-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fe31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fe31-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="8fe31-106">[out] Ukazatel na identifikátor GUID procesu, ve kterém se objekt nachází.</span><span class="sxs-lookup"><span data-stu-id="8fe31-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="8fe31-107">[out] Ukazatel na ID objektu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8fe31-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="8fe31-108">[out] Ukazatel na indexu objektu v modelu COM classic tabulce.</span><span class="sxs-lookup"><span data-stu-id="8fe31-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fe31-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fe31-109">Remarks</span></span>  
 <span data-ttu-id="8fe31-110">Identitu spravovaného objektu obsahuje proces identifikátor GUID ID domény aplikace a index objektu v COM classic v-table.</span><span class="sxs-lookup"><span data-stu-id="8fe31-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe31-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fe31-111">Requirements</span></span>  
 <span data-ttu-id="8fe31-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe31-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe31-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8fe31-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8fe31-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fe31-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8fe31-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe31-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe31-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fe31-116">See also</span></span>
- [<span data-ttu-id="8fe31-117">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fe31-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
