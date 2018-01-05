---
title: "IEnumDefinitionIdentity – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumDefinitionIdentity
helpviewer_keywords: IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79e2a35a455407715a05e826d31c5d5ab05a02ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="45016-102">IEnumDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45016-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="45016-103">Slouží jako enumerátoru pro kolekci `IDefinitionIdentity` objekty.</span><span class="sxs-lookup"><span data-stu-id="45016-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45016-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45016-104">Syntax</span></span>  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="45016-105">Metody</span><span class="sxs-lookup"><span data-stu-id="45016-105">Methods</span></span>  
  
|<span data-ttu-id="45016-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="45016-106">Method</span></span>|<span data-ttu-id="45016-107">Popis</span><span class="sxs-lookup"><span data-stu-id="45016-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="45016-108">Získá ukazatele rozhraní na nový `IEnumDefinitionIdentity` objekt, který obsahuje členy stejné jako to `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="45016-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="45016-109">Získá zadaný počet `IDefinitionIdentity` objektů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="45016-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="45016-110">Ukazatel instrukce přesune na začátku tohoto `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="45016-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="45016-111">Ukazatel instrukce dál přesune o zadaný počet elementů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="45016-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45016-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45016-112">Requirements</span></span>  
 <span data-ttu-id="45016-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45016-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45016-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="45016-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="45016-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45016-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45016-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="45016-116">See Also</span></span>  
 [<span data-ttu-id="45016-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="45016-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="45016-118">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45016-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
