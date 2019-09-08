---
title: IDefinitionIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84c595bfdcca84ee43a53e2ea913cc978ae0953e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796525"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="35852-102">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35852-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="35852-103">Představuje jedinečný podpis kódu, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="35852-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35852-104">Metody</span><span class="sxs-lookup"><span data-stu-id="35852-104">Methods</span></span>  
  
|<span data-ttu-id="35852-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="35852-105">Method</span></span>|<span data-ttu-id="35852-106">Popis</span><span class="sxs-lookup"><span data-stu-id="35852-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="35852-107">Získá ukazatel rozhraní na nový `IDefinitionIdentity` objekt, který je identický `IDefinitionIdentity`s výjimkou určených změn atributů.</span><span class="sxs-lookup"><span data-stu-id="35852-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="35852-108">Získá ukazatel rozhraní na objekt [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) , který obsahuje atributy přidružené k tomuto `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="35852-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="35852-109">Získá hodnotu atributu se zadaným názvem v určeném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="35852-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="35852-110">Nastaví atribut, který má zadaný název v zadaném oboru názvů na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="35852-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="35852-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35852-111">Requirements</span></span>  
 <span data-ttu-id="35852-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35852-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35852-113">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="35852-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="35852-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35852-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35852-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35852-115">See also</span></span>

- [<span data-ttu-id="35852-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="35852-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
