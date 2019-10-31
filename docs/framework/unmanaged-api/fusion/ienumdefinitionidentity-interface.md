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
ms.openlocfilehash: 09c6431ec885c8b797dc9bb5f5c3ffe21890ccc7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107944"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="58940-102">IEnumDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58940-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="58940-103">Slouží jako enumerátor pro kolekci `IDefinitionIdentity` objektů.</span><span class="sxs-lookup"><span data-stu-id="58940-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58940-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58940-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="58940-105">Metody</span><span class="sxs-lookup"><span data-stu-id="58940-105">Methods</span></span>  
  
|<span data-ttu-id="58940-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="58940-106">Method</span></span>|<span data-ttu-id="58940-107">Popis</span><span class="sxs-lookup"><span data-stu-id="58940-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="58940-108">Získá ukazatel rozhraní na nový objekt `IEnumDefinitionIdentity`, který obsahuje stejné členy jako tento `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="58940-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="58940-109">Získá zadaný počet `IDefinitionIdentity` objektů, počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="58940-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="58940-110">Přesune ukazatel na instrukci na začátek tohoto `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="58940-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="58940-111">Přesune ukazatel na instrukci směrem nahoru o zadaný počet prvků od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="58940-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58940-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58940-112">Requirements</span></span>  
 <span data-ttu-id="58940-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58940-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58940-114">**Hlavička:** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="58940-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="58940-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58940-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58940-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58940-116">See also</span></span>

- [<span data-ttu-id="58940-117">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="58940-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="58940-118">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58940-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
