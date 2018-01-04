---
title: "IReferenceAppId – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="9e572-102">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e572-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="9e572-103">Představuje odkaz na jedinečný identifikátor pro aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="9e572-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e572-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9e572-104">Methods</span></span>  
  
|<span data-ttu-id="9e572-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e572-105">Method</span></span>|<span data-ttu-id="9e572-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9e572-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="9e572-107">Získá ukazatel na řetězcovou reprezentaci identifikátor kódu pro aplikaci odkazuje toto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="9e572-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="9e572-108">Nastaví identifikátor kódu pro aplikace, které odkazuje toto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="9e572-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="9e572-109">Získá ukazatele rozhraní k `IEnumReferenceIdentity` obsahující instance `IReferenceIdentity` instancí, které představují členy této `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="9e572-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="9e572-110">Získá ukazatel na řetězcová reprezentace identifikátoru tokenu pro toto předplatné `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="9e572-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="9e572-111">Nastaví identifikátor tokenu pro přihlášení k odběru do tohoto `IReferenceAppId` zadaným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="9e572-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e572-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e572-112">Requirements</span></span>  
 <span data-ttu-id="9e572-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e572-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e572-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="9e572-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9e572-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e572-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e572-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e572-116">See Also</span></span>  
 [<span data-ttu-id="9e572-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="9e572-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="9e572-118">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e572-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="9e572-119">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e572-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
