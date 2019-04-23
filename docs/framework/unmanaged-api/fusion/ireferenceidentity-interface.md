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
ms.openlocfilehash: dd46ea26532074c9ea42da4d07a38ed583aad076
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220159"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="5a2d7-102">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a2d7-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="5a2d7-103">Představuje odkaz na jedinečný podpis kódu objektu.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a2d7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5a2d7-104">Methods</span></span>  
  
|<span data-ttu-id="5a2d7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5a2d7-105">Method</span></span>|<span data-ttu-id="5a2d7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5a2d7-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="5a2d7-107">Získá ukazatel rozhraní na nový `IReferenceIdentity` instanci, která se shoduje s tím `IReferenceIdentity`, s výjimkou změn zadaného atributu.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="5a2d7-108">Získá ukazatel rozhraní k `IEnumIDENTITY_ATTRIBUTE` instance, která obsahuje atributy přidružené k tomuto `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="5a2d7-109">Získá hodnotu atributu v určeném oboru názvů se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="5a2d7-110">Nastaví atribut, který má zadaný obor názvů a zadaným názvem se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="5a2d7-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a2d7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a2d7-111">Requirements</span></span>  
 <span data-ttu-id="5a2d7-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a2d7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a2d7-113">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="5a2d7-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="5a2d7-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a2d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2d7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a2d7-115">See also</span></span>

- [<span data-ttu-id="5a2d7-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="5a2d7-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="5a2d7-117">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a2d7-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
