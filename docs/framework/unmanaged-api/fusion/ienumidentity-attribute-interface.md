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
ms.openlocfilehash: d725228f2a7359d415673fdcb90d0cabae1a40be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175523"
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="2370a-102">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2370a-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="2370a-103">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="2370a-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2370a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2370a-104">Methods</span></span>  
  
|<span data-ttu-id="2370a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2370a-105">Method</span></span>|<span data-ttu-id="2370a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2370a-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="2370a-107">Získá ukazatel rozhraní na nový `IEnumIDENTITY_ATTRIBUTE` , která obsahuje stejné členy jako to `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="2370a-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="2370a-108">Zapíše data obsažená v elementech této `IEnumIDENTITY_ATTRIBUTE` do vyrovnávací paměti zadaná data.</span><span class="sxs-lookup"><span data-stu-id="2370a-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="2370a-109">Získá zadaný počet atributů, od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="2370a-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="2370a-110">Přesune ukazatel na instrukci na začátek `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="2370a-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="2370a-111">Přesune ukazatele na instrukci vpřed o zadaný počet prvků počínaje od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="2370a-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2370a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2370a-112">Requirements</span></span>  
 <span data-ttu-id="2370a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2370a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2370a-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2370a-114">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="2370a-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2370a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2370a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2370a-116">See also</span></span>

- [<span data-ttu-id="2370a-117">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="2370a-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
