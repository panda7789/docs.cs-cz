---
title: IReferenceAppId – rozhraní
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157193"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="dda35-102">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dda35-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="dda35-103">Představuje odkaz na jedinečný identifikátor pro aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="dda35-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dda35-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dda35-104">Methods</span></span>  
  
|<span data-ttu-id="dda35-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dda35-105">Method</span></span>|<span data-ttu-id="dda35-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dda35-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="dda35-107">Získá ukazatel na řetězcovou reprezentaci identifikátoru kódu pro aplikace, které odkazuje tato `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="dda35-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="dda35-108">Nastaví kód identifikátor pro aplikaci odkazovaná tímto objektem `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="dda35-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="dda35-109">Získá ukazatel rozhraní k `IEnumReferenceIdentity` obsahující instance `IReferenceIdentity` instancí, které představují členy tohoto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="dda35-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="dda35-110">Získá ukazatel na řetězcovou reprezentaci identifikátoru token pro přihlášení k odběru této `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="dda35-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="dda35-111">Nastaví identifikátor token pro přihlášení k odběru této `IReferenceAppId` hodnotu zadaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="dda35-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dda35-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dda35-112">Requirements</span></span>  
 <span data-ttu-id="dda35-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda35-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda35-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="dda35-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="dda35-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda35-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dda35-116">See also</span></span>

- [<span data-ttu-id="dda35-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="dda35-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="dda35-118">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dda35-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [<span data-ttu-id="dda35-119">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dda35-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
