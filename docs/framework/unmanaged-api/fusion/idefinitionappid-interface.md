---
title: "IDefinitionAppId – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 247edbe300bbb93ddbdd4260109999fd33b08006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="b69da-102">IDefinitionAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b69da-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="b69da-103">Představuje jedinečný identifikátor pro kód, který definuje aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="b69da-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b69da-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b69da-104">Methods</span></span>  
  
|<span data-ttu-id="b69da-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b69da-105">Method</span></span>|<span data-ttu-id="b69da-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b69da-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="b69da-107">Získá formátovaný řetězec, který představuje kód v tomto `IDefinitionAppId` objektu.</span><span class="sxs-lookup"><span data-stu-id="b69da-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="b69da-108">Nastaví kód to `IDefinitionAppId` objekt do zadané řetězcové hodnoty ve formátu.</span><span class="sxs-lookup"><span data-stu-id="b69da-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="b69da-109">Získá ukazatele rozhraní k [ienumdefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objekt, který obsahuje sestavení v aktuální cestě aplikace.</span><span class="sxs-lookup"><span data-stu-id="b69da-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="b69da-110">Nastaví cestu k aplikaci pro sestavení v aktuálním oboru na hodnotu odkazuje zadaný [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="b69da-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="b69da-111">Získá ukazatel na řetězcová reprezentace identifikátoru tokenu pro toto předplatné `IDefinitionAppId` objektu.</span><span class="sxs-lookup"><span data-stu-id="b69da-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="b69da-112">Nastaví identifikátor tokenu pro přihlášení k odběru do tohoto `IDefinitionAppId` objekt, který chcete je zadaná řetězcová hodnota.</span><span class="sxs-lookup"><span data-stu-id="b69da-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b69da-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b69da-113">Requirements</span></span>  
 <span data-ttu-id="b69da-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b69da-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b69da-115">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="b69da-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b69da-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b69da-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b69da-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b69da-117">See Also</span></span>  
 [<span data-ttu-id="b69da-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="b69da-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
