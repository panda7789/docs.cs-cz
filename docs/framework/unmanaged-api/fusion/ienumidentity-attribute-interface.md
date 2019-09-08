---
title: IEnumIDENTITY_ATTRIBUTE – rozhraní
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796464"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="7ea59-102">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ea59-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="7ea59-103">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="7ea59-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ea59-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ea59-104">Methods</span></span>  
  
|<span data-ttu-id="7ea59-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ea59-105">Method</span></span>|<span data-ttu-id="7ea59-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7ea59-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="7ea59-107">Získá ukazatel rozhraní na nový `IEnumIDENTITY_ATTRIBUTE` , který obsahuje stejné členy jako to. `IEnumIDENTITY_ATTRIBUTE`</span><span class="sxs-lookup"><span data-stu-id="7ea59-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="7ea59-108">Zapíše data obsažená v prvcích tohoto `IEnumIDENTITY_ATTRIBUTE` typu do zadané datové vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7ea59-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="7ea59-109">Získá zadaný počet atributů od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="7ea59-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="7ea59-110">Přesune ukazatel na instrukci na začátek tohoto `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="7ea59-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="7ea59-111">Přesune ukazatel na instrukci směrem nahoru o zadaný počet prvků od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="7ea59-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ea59-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ea59-112">Requirements</span></span>  
 <span data-ttu-id="7ea59-113">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ea59-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ea59-114">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="7ea59-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7ea59-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ea59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea59-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ea59-116">See also</span></span>

- [<span data-ttu-id="7ea59-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="7ea59-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
