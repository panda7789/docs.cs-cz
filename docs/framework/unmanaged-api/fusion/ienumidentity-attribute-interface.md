---
title: "IEnumIDENTITY_ATTRIBUTE – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc77f2106f5063b8db25f375c354a15f9f936e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="71bde-102">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71bde-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="71bde-103">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="71bde-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71bde-104">Metody</span><span class="sxs-lookup"><span data-stu-id="71bde-104">Methods</span></span>  
  
|<span data-ttu-id="71bde-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="71bde-105">Method</span></span>|<span data-ttu-id="71bde-106">Popis</span><span class="sxs-lookup"><span data-stu-id="71bde-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="71bde-107">Získá ukazatele rozhraní na nový `IEnumIDENTITY_ATTRIBUTE` obsahující členy stejné jako to `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="71bde-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="71bde-108">Zapíše data obsažená v elementech tohoto `IEnumIDENTITY_ATTRIBUTE` do vyrovnávací paměti zadaná data.</span><span class="sxs-lookup"><span data-stu-id="71bde-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="71bde-109">Získá zadaný počet atributů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="71bde-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="71bde-110">Ukazatel instrukce přesune na začátku tohoto `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="71bde-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="71bde-111">Ukazatel instrukce dál přesune o zadaný počet elementů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="71bde-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71bde-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71bde-112">Requirements</span></span>  
 <span data-ttu-id="71bde-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71bde-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71bde-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="71bde-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="71bde-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71bde-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71bde-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="71bde-116">See Also</span></span>  
 [<span data-ttu-id="71bde-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="71bde-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
