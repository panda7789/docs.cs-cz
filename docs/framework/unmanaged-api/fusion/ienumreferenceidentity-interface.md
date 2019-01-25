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
ms.openlocfilehash: 1f2ea9d0e20cb67cc36d0b5883e483ce98941b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743215"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="c3095-102">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3095-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="c3095-103">Slouží jako enumerátor pro kolekci `IReferenceIdentity` objekty.</span><span class="sxs-lookup"><span data-stu-id="c3095-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3095-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c3095-104">Methods</span></span>  
  
|<span data-ttu-id="c3095-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c3095-105">Method</span></span>|<span data-ttu-id="c3095-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c3095-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="c3095-107">Získá ukazatel rozhraní na nový `IEnumReferenceIdentity` , která obsahuje stejné členy jako to `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="c3095-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="c3095-108">Získá zadaný počet `IReferenceIdentity` objektů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="c3095-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="c3095-109">Přesune ukazatel na instrukci na začátek `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="c3095-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="c3095-110">Přesune ukazatele na instrukci vpřed o zadaný počet prvků počínaje od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="c3095-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3095-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3095-111">Requirements</span></span>  
 <span data-ttu-id="c3095-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3095-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3095-113">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="c3095-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c3095-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3095-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3095-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3095-115">See also</span></span>
- [<span data-ttu-id="c3095-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="c3095-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="c3095-117">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3095-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
