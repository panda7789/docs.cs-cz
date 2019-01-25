---
title: IEnumDefinitionIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3ff37acd9b4dffe80112f0a0ebe9c9cd86ae66f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668444"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="46189-102">IEnumDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46189-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="46189-103">Slouží jako enumerátoru pro kolekci `IDefinitionIdentity` objekty.</span><span class="sxs-lookup"><span data-stu-id="46189-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46189-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46189-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="46189-105">Metody</span><span class="sxs-lookup"><span data-stu-id="46189-105">Methods</span></span>  
  
|<span data-ttu-id="46189-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="46189-106">Method</span></span>|<span data-ttu-id="46189-107">Popis</span><span class="sxs-lookup"><span data-stu-id="46189-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="46189-108">Získá ukazatel rozhraní na nový `IEnumDefinitionIdentity` objekt, který obsahuje stejné členy jako to `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="46189-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="46189-109">Získá zadaný počet `IDefinitionIdentity` objektů, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="46189-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="46189-110">Přesune ukazatel na instrukci na začátek `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="46189-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="46189-111">Přesune ukazatele na instrukci vpřed o zadaný počet prvků počínaje od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="46189-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46189-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46189-112">Requirements</span></span>  
 <span data-ttu-id="46189-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46189-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46189-114">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="46189-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="46189-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46189-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46189-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46189-116">See also</span></span>
- [<span data-ttu-id="46189-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="46189-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="46189-118">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46189-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
