---
title: "IEnumIDENTITY_ATTRIBUTE – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumIDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords: IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f88e400556421e0908e0a0b115f66ec3221124c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="f381e-102">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f381e-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="f381e-103">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="f381e-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f381e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f381e-104">Methods</span></span>  
  
|<span data-ttu-id="f381e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f381e-105">Method</span></span>|<span data-ttu-id="f381e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f381e-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="f381e-107">Získá ukazatele rozhraní na nový `IEnumIDENTITY_ATTRIBUTE` obsahující členy stejné jako to `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="f381e-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="f381e-108">Zapíše data obsažená v elementech tohoto `IEnumIDENTITY_ATTRIBUTE` do vyrovnávací paměti zadaná data.</span><span class="sxs-lookup"><span data-stu-id="f381e-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="f381e-109">Získá zadaný počet atributů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="f381e-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="f381e-110">Ukazatel instrukce přesune na začátku tohoto `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="f381e-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="f381e-111">Ukazatel instrukce dál přesune o zadaný počet elementů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="f381e-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f381e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f381e-112">Requirements</span></span>  
 <span data-ttu-id="f381e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f381e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f381e-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="f381e-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f381e-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f381e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f381e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f381e-116">See Also</span></span>  
 [<span data-ttu-id="f381e-117">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="f381e-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
