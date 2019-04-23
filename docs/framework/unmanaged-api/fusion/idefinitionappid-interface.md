---
title: IDefinitionAppId – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd705ef549de3a8018efe731ef8735ef7b6b915
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083176"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="d83ff-102">IDefinitionAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d83ff-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="d83ff-103">Představuje jedinečný identifikátor pro kód, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="d83ff-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d83ff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d83ff-104">Methods</span></span>  
  
|<span data-ttu-id="d83ff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d83ff-105">Method</span></span>|<span data-ttu-id="d83ff-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d83ff-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="d83ff-107">Získá formátovaný řetězec, který představuje kód v tomto `IDefinitionAppId` objektu.</span><span class="sxs-lookup"><span data-stu-id="d83ff-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="d83ff-108">Nastaví kód tohoto `IDefinitionAppId` objekt do zadané řetězcové hodnoty ve formátu.</span><span class="sxs-lookup"><span data-stu-id="d83ff-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="d83ff-109">Získá ukazatel rozhraní k [ienumdefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objekt, který obsahuje sestavení v aktuální cestě aplikace.</span><span class="sxs-lookup"><span data-stu-id="d83ff-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="d83ff-110">Nastaví cestu k aplikaci pro sestavení v aktuálním oboru na hodnotu odkazuje zadaný [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="d83ff-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="d83ff-111">Získá ukazatel na řetězcovou reprezentaci identifikátoru token pro přihlášení k odběru této `IDefinitionAppId` objektu.</span><span class="sxs-lookup"><span data-stu-id="d83ff-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="d83ff-112">Nastaví identifikátor token pro přihlášení k odběru této `IDefinitionAppId` zadaná řetězcová hodnota objektu.</span><span class="sxs-lookup"><span data-stu-id="d83ff-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d83ff-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d83ff-113">Requirements</span></span>  
 <span data-ttu-id="d83ff-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83ff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83ff-115">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="d83ff-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="d83ff-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83ff-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d83ff-117">See also</span></span>

- [<span data-ttu-id="d83ff-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="d83ff-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
