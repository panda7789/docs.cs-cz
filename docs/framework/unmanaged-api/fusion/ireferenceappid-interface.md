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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131651"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="53582-102">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53582-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="53582-103">Představuje odkaz na jedinečný identifikátor aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="53582-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53582-104">Metody</span><span class="sxs-lookup"><span data-stu-id="53582-104">Methods</span></span>  
  
|<span data-ttu-id="53582-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="53582-105">Method</span></span>|<span data-ttu-id="53582-106">Popis</span><span class="sxs-lookup"><span data-stu-id="53582-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="53582-107">Získá ukazatel na řetězcovou reprezentaci identifikátoru kódu pro aplikaci, na kterou odkazuje tento `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="53582-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="53582-108">Nastaví identifikátor kódu pro aplikaci, na kterou odkazuje tento `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="53582-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="53582-109">Získá ukazatel rozhraní na instanci `IEnumReferenceIdentity` obsahující `IReferenceIdentity` instance, které reprezentují členy tohoto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="53582-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="53582-110">Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr tohoto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="53582-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="53582-111">Nastaví identifikátor tokenu pro odběr tohoto `IReferenceAppId` na zadanou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="53582-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53582-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53582-112">Requirements</span></span>  
 <span data-ttu-id="53582-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53582-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53582-114">**Hlavička:** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="53582-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="53582-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53582-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53582-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53582-116">See also</span></span>

- [<span data-ttu-id="53582-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="53582-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="53582-118">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53582-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="53582-119">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53582-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
