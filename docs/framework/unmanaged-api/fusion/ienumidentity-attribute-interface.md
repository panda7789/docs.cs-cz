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
ms.openlocfilehash: 7e6bc57fb470a5c12549bb5f9445ecf1551425a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107845"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="ca539-102">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca539-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="ca539-103">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="ca539-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca539-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca539-104">Methods</span></span>  
  
|<span data-ttu-id="ca539-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca539-105">Method</span></span>|<span data-ttu-id="ca539-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ca539-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="ca539-107">Získá ukazatel rozhraní na nový `IEnumIDENTITY_ATTRIBUTE`, který obsahuje stejné členy jako tento `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="ca539-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="ca539-108">Zapíše data obsažená v prvcích tohoto `IEnumIDENTITY_ATTRIBUTE` do zadané vyrovnávací paměti dat.</span><span class="sxs-lookup"><span data-stu-id="ca539-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="ca539-109">Získá zadaný počet atributů od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="ca539-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="ca539-110">Přesune ukazatel na instrukci na začátek tohoto `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="ca539-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="ca539-111">Přesune ukazatel na instrukci směrem nahoru o zadaný počet prvků od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="ca539-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca539-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca539-112">Requirements</span></span>  
 <span data-ttu-id="ca539-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca539-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca539-114">**Hlavička:** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="ca539-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ca539-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca539-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca539-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca539-116">See also</span></span>

- [<span data-ttu-id="ca539-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="ca539-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
