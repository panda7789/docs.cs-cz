---
title: IReferenceIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796353"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="3b477-102">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b477-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="3b477-103">Představuje odkaz na jedinečný podpis objektu kódu.</span><span class="sxs-lookup"><span data-stu-id="3b477-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b477-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3b477-104">Methods</span></span>  
  
|<span data-ttu-id="3b477-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b477-105">Method</span></span>|<span data-ttu-id="3b477-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3b477-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="3b477-107">Získá ukazatel rozhraní na novou `IReferenceIdentity` instanci, která je stejná jako tato `IReferenceIdentity`, s výjimkou změny zadaného atributu.</span><span class="sxs-lookup"><span data-stu-id="3b477-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="3b477-108">Získá ukazatel rozhraní na `IEnumIDENTITY_ATTRIBUTE` instanci, která obsahuje atributy přidružené k tomuto. `IReferenceIdentity`</span><span class="sxs-lookup"><span data-stu-id="3b477-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="3b477-109">Získá hodnotu atributu v určeném oboru názvů se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="3b477-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="3b477-110">Nastaví atribut, který má zadaný obor názvů a zadaný název na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3b477-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b477-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b477-111">Requirements</span></span>  
 <span data-ttu-id="3b477-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b477-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b477-113">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="3b477-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3b477-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b477-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b477-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b477-115">See also</span></span>

- [<span data-ttu-id="3b477-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="3b477-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="3b477-117">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b477-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
