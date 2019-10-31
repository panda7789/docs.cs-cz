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
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108202"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="1454b-102">IDefinitionAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1454b-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="1454b-103">Představuje jedinečný identifikátor kódu, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="1454b-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1454b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1454b-104">Methods</span></span>  
  
|<span data-ttu-id="1454b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1454b-105">Method</span></span>|<span data-ttu-id="1454b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1454b-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="1454b-107">Načte formátovaný řetězec, který představuje kód v tomto objektu `IDefinitionAppId`.</span><span class="sxs-lookup"><span data-stu-id="1454b-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="1454b-108">Nastaví kód tohoto objektu `IDefinitionAppId` na zadanou naformátovanou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="1454b-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="1454b-109">Získá ukazatel rozhraní na objekt [IEnumDefinitionIdentity –](ienumdefinitionidentity-interface.md) , který obsahuje sestavení v aktuální cestě aplikace.</span><span class="sxs-lookup"><span data-stu-id="1454b-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="1454b-110">Nastaví cestu aplikace pro sestavení v aktuálním rozsahu na hodnotu, na kterou odkazuje zadaný objekt [IDefinitionIdentity –](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1454b-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="1454b-111">Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr tohoto objektu `IDefinitionAppId`.</span><span class="sxs-lookup"><span data-stu-id="1454b-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="1454b-112">Nastaví identifikátor tokenu pro odběr tohoto `IDefinitionAppId` objektu na zadanou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="1454b-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1454b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1454b-113">Requirements</span></span>  
 <span data-ttu-id="1454b-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1454b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1454b-115">**Hlavička:** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="1454b-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1454b-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1454b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1454b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1454b-117">See also</span></span>

- [<span data-ttu-id="1454b-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="1454b-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
