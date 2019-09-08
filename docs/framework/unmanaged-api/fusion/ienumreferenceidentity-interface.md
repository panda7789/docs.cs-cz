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
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796440"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="0bdea-102">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bdea-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="0bdea-103">Slouží jako enumerátor pro kolekci `IReferenceIdentity` objektů.</span><span class="sxs-lookup"><span data-stu-id="0bdea-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bdea-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0bdea-104">Methods</span></span>  
  
|<span data-ttu-id="0bdea-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0bdea-105">Method</span></span>|<span data-ttu-id="0bdea-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0bdea-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="0bdea-107">Získá ukazatel rozhraní na nový `IEnumReferenceIdentity` , který obsahuje stejné členy jako to. `IEnumReferenceIdentity`</span><span class="sxs-lookup"><span data-stu-id="0bdea-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="0bdea-108">Získá zadaný počet `IReferenceIdentity` objektů od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="0bdea-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="0bdea-109">Přesune ukazatel na instrukci na začátek tohoto `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="0bdea-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="0bdea-110">Přesune ukazatel na instrukci směrem nahoru o zadaný počet prvků od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="0bdea-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bdea-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bdea-111">Requirements</span></span>  
 <span data-ttu-id="0bdea-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bdea-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bdea-113">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="0bdea-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0bdea-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bdea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bdea-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bdea-115">See also</span></span>

- [<span data-ttu-id="0bdea-116">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="0bdea-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="0bdea-117">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bdea-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
