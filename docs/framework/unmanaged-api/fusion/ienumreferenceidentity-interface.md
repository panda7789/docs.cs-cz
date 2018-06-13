---
title: IEnumReferenceIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ebc9fe36955bac8b93ec95e9a55fc8ac1197d9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429118"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="dcdf0-102">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcdf0-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="dcdf0-103">Slouží jako enumerátor pro kolekci `IReferenceIdentity` objekty.</span><span class="sxs-lookup"><span data-stu-id="dcdf0-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcdf0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dcdf0-104">Methods</span></span>  
  
|<span data-ttu-id="dcdf0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dcdf0-105">Method</span></span>|<span data-ttu-id="dcdf0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dcdf0-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="dcdf0-107">Získá ukazatele rozhraní na nový `IEnumReferenceIdentity` obsahující členy stejné jako to `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="dcdf0-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="dcdf0-108">Získá zadaný počet `IReferenceIdentity` objektů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="dcdf0-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="dcdf0-109">Ukazatel instrukce přesune na začátku tohoto `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="dcdf0-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="dcdf0-110">Ukazatel instrukce dál přesune o zadaný počet elementů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="dcdf0-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcdf0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcdf0-111">Requirements</span></span>  
 <span data-ttu-id="dcdf0-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcdf0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcdf0-113">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="dcdf0-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="dcdf0-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcdf0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdf0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcdf0-115">See Also</span></span>  
 [<span data-ttu-id="dcdf0-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="dcdf0-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="dcdf0-117">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcdf0-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
