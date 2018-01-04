---
title: "IDefinitionIdentity – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionIdentity
helpviewer_keywords: IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b074ae2a0a4e4e65f0402ff35888b557b00dd071
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="cfd45-102">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfd45-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="cfd45-103">Představuje jedinečné podpis kód, který definuje aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="cfd45-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfd45-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cfd45-104">Methods</span></span>  
  
|<span data-ttu-id="cfd45-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cfd45-105">Method</span></span>|<span data-ttu-id="cfd45-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cfd45-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="cfd45-107">Získá ukazatele rozhraní na nový `IDefinitionIdentity` objekt, který je stejný jako to `IDefinitionIdentity`, s výjimkou změny zadaného atributu.</span><span class="sxs-lookup"><span data-stu-id="cfd45-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="cfd45-108">Získá ukazatele rozhraní k [ienumidentity_attribute –](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) objekt obsahující atributy přidružené k tomuto `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="cfd45-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="cfd45-109">Získá hodnotu atributu se zadaným názvem v určeném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cfd45-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="cfd45-110">Nastaví atribut, který má zadaný název v určeném oboru názvů se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cfd45-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cfd45-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfd45-111">Requirements</span></span>  
 <span data-ttu-id="cfd45-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfd45-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfd45-113">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="cfd45-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="cfd45-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfd45-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd45-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfd45-115">See Also</span></span>  
 [<span data-ttu-id="cfd45-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="cfd45-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
