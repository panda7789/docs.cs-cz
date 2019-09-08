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
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796365"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="57c8c-102">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57c8c-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="57c8c-103">Představuje odkaz na jedinečný identifikátor aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="57c8c-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57c8c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57c8c-104">Methods</span></span>  
  
|<span data-ttu-id="57c8c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57c8c-105">Method</span></span>|<span data-ttu-id="57c8c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="57c8c-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="57c8c-107">Získá ukazatel na řetězcovou reprezentaci identifikátoru kódu pro aplikaci, na kterou se odkazuje `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="57c8c-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="57c8c-108">Nastaví identifikátor kódu aplikace, na kterou se odkazuje `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="57c8c-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="57c8c-109">Získá ukazatel rozhraní na `IEnumReferenceIdentity` instanci `IReferenceIdentity` obsahující instance `IReferenceAppId`, které reprezentují členy.</span><span class="sxs-lookup"><span data-stu-id="57c8c-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="57c8c-110">Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="57c8c-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="57c8c-111">Nastaví identifikátor tokenu pro odběr `IReferenceAppId` na zadanou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="57c8c-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57c8c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57c8c-112">Requirements</span></span>  
 <span data-ttu-id="57c8c-113">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57c8c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c8c-114">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="57c8c-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="57c8c-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c8c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c8c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57c8c-116">See also</span></span>

- [<span data-ttu-id="57c8c-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="57c8c-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="57c8c-118">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57c8c-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="57c8c-119">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57c8c-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
