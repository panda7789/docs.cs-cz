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
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="cde76-102">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cde76-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="cde76-103">Představuje odkaz na jedinečný identifikátor pro aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="cde76-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cde76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cde76-104">Methods</span></span>  
  
|<span data-ttu-id="cde76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cde76-105">Method</span></span>|<span data-ttu-id="cde76-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cde76-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="cde76-107">Získá ukazatel na řetězcovou reprezentaci identifikátor kódu pro aplikaci odkazuje toto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="cde76-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="cde76-108">Nastaví identifikátor kódu pro aplikace, které odkazuje toto `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="cde76-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="cde76-109">Získá ukazatele rozhraní k `IEnumReferenceIdentity` obsahující instance `IReferenceIdentity` instancí, které představují členy této `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="cde76-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="cde76-110">Získá ukazatel na řetězcová reprezentace identifikátoru tokenu pro toto předplatné `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="cde76-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="cde76-111">Nastaví identifikátor tokenu pro přihlášení k odběru do tohoto `IReferenceAppId` zadaným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="cde76-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cde76-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cde76-112">Requirements</span></span>  
 <span data-ttu-id="cde76-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cde76-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cde76-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="cde76-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="cde76-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cde76-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde76-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cde76-116">See Also</span></span>  
 [<span data-ttu-id="cde76-117">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="cde76-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="cde76-118">Ienumreferenceidentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cde76-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="cde76-119">Ireferenceidentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cde76-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
