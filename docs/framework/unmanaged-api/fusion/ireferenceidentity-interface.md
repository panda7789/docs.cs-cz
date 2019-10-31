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
ms.openlocfilehash: 8f6a117d1e2fe76c271b0b014e6079370c8b4fe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127068"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="1b933-102">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b933-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="1b933-103">Představuje odkaz na jedinečný podpis objektu kódu.</span><span class="sxs-lookup"><span data-stu-id="1b933-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b933-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1b933-104">Methods</span></span>  
  
|<span data-ttu-id="1b933-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1b933-105">Method</span></span>|<span data-ttu-id="1b933-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1b933-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="1b933-107">Získá ukazatel rozhraní na novou instanci `IReferenceIdentity`, která je shodná s tímto `IReferenceIdentity`, s výjimkou zadaných změn atributů.</span><span class="sxs-lookup"><span data-stu-id="1b933-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="1b933-108">Získá ukazatel rozhraní na instanci `IEnumIDENTITY_ATTRIBUTE`, která obsahuje atributy přidružené k tomuto `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="1b933-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="1b933-109">Získá hodnotu atributu v určeném oboru názvů se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="1b933-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="1b933-110">Nastaví atribut, který má zadaný obor názvů a zadaný název na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b933-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b933-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b933-111">Requirements</span></span>  
 <span data-ttu-id="1b933-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b933-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b933-113">**Hlavička:** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="1b933-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1b933-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b933-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b933-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b933-115">See also</span></span>

- [<span data-ttu-id="1b933-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="1b933-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1b933-117">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b933-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
