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
ms.openlocfilehash: 8c884569a452fb2985713956f942205cda6ea1ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141243"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="0896f-102">IManagedObject::GetObjectIdentity – metoda</span><span class="sxs-lookup"><span data-stu-id="0896f-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="0896f-103">Získá identitu tohoto spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="0896f-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0896f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0896f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0896f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0896f-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="0896f-106">mimo Ukazatel na identifikátor GUID procesu, ve kterém se nachází objekt.</span><span class="sxs-lookup"><span data-stu-id="0896f-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="0896f-107">mimo Ukazatel na ID domény aplikace objektu.</span><span class="sxs-lookup"><span data-stu-id="0896f-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="0896f-108">mimo Ukazatel na index objektu v tabulce modelu COM Classic v-Table.</span><span class="sxs-lookup"><span data-stu-id="0896f-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0896f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0896f-109">Remarks</span></span>  
 <span data-ttu-id="0896f-110">Identita spravovaného objektu obsahuje identifikátor GUID procesu, ID domény aplikace a index objektu v tabulce modelu COM Classic v-Table.</span><span class="sxs-lookup"><span data-stu-id="0896f-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0896f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0896f-111">Requirements</span></span>  
 <span data-ttu-id="0896f-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0896f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0896f-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0896f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0896f-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0896f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0896f-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0896f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0896f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0896f-116">See also</span></span>

- [<span data-ttu-id="0896f-117">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0896f-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
