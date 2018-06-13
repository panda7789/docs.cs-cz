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
ms.openlocfilehash: 2484fa61c03b95e7cbdb452b92a68a2049701374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429514"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="8ab71-102">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ab71-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="8ab71-103">Představuje odkaz na jedinečný identifikátor pro aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="8ab71-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ab71-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8ab71-104">Methods</span></span>  
  
|<span data-ttu-id="8ab71-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8ab71-105">Method</span></span>|<span data-ttu-id="8ab71-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8ab71-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="8ab71-107">Získá ukazatel na řetězcovou reprezentaci identifikátor kódu pro aplikaci odkazuje toto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="8ab71-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="8ab71-108">Nastaví identifikátor kódu pro aplikace, které odkazuje toto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="8ab71-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="8ab71-109">Získá ukazatele rozhraní k `IEnumReferenceIdentity` obsahující instance `IReferenceIdentity` instancí, které představují členy této `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="8ab71-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="8ab71-110">Získá ukazatel na řetězcová reprezentace identifikátoru tokenu pro toto předplatné `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="8ab71-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="8ab71-111">Nastaví identifikátor tokenu pro přihlášení k odběru do tohoto `IReferenceAppId` zadaným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="8ab71-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ab71-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ab71-112">Requirements</span></span>  
 <span data-ttu-id="8ab71-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ab71-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ab71-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="8ab71-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="8ab71-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ab71-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab71-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ab71-116">See Also</span></span>  
 [<span data-ttu-id="8ab71-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="8ab71-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="8ab71-118">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ab71-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="8ab71-119">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ab71-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
