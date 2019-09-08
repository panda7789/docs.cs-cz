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
ms.openlocfilehash: 929909a7f2c4fa1799c8fed94787b8f853c7eac2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796518"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="c4c9d-102">IDefinitionAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4c9d-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="c4c9d-103">Představuje jedinečný identifikátor kódu, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="c4c9d-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4c9d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c4c9d-104">Methods</span></span>  
  
|<span data-ttu-id="c4c9d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4c9d-105">Method</span></span>|<span data-ttu-id="c4c9d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c4c9d-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="c4c9d-107">Načte formátovaný řetězec, který představuje kód v tomto `IDefinitionAppId` objektu.</span><span class="sxs-lookup"><span data-stu-id="c4c9d-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="c4c9d-108">Nastaví kód tohoto `IDefinitionAppId` objektu na zadanou naformátovanou řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4c9d-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="c4c9d-109">Získá ukazatel rozhraní na objekt [IEnumDefinitionIdentity –](ienumdefinitionidentity-interface.md) , který obsahuje sestavení v aktuální cestě aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4c9d-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="c4c9d-110">Nastaví cestu aplikace pro sestavení v aktuálním rozsahu na hodnotu, na kterou odkazuje zadaný objekt [IDefinitionIdentity –](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c4c9d-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="c4c9d-111">Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr tohoto `IDefinitionAppId` objektu.</span><span class="sxs-lookup"><span data-stu-id="c4c9d-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="c4c9d-112">Nastaví identifikátor tokenu pro odběr na tento `IDefinitionAppId` objekt na zadanou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="c4c9d-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4c9d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4c9d-113">Requirements</span></span>  
 <span data-ttu-id="c4c9d-114">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4c9d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c9d-115">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="c4c9d-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c4c9d-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c9d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4c9d-117">See also</span></span>

- [<span data-ttu-id="c4c9d-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="c4c9d-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
