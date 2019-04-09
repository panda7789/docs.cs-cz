---
title: EnumCustomAttributes – metoda
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b419962982fc80591ed565cceb28afb88a39495e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199138"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="e8bfc-102">EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="e8bfc-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="e8bfc-103">Načte vlastní atributy úrovně sestavení.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8bfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8bfc-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8bfc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8bfc-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e8bfc-106">Popisovač výčtu.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="e8bfc-107">Typ atributů, které chcete vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="e8bfc-108">Použití `mdTokenNill` pro všechny atributy.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="e8bfc-109">Přijímá tokeny vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e8bfc-110">Určuje velikost `rCustomValues` pole.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="e8bfc-111">Volitelně přijímá počet hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8bfc-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e8bfc-112">Return Value</span></span>  
 <span data-ttu-id="e8bfc-113">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="e8bfc-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8bfc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8bfc-114">Requirements</span></span>  
 <span data-ttu-id="e8bfc-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="e8bfc-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8bfc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8bfc-116">See also</span></span>

- [<span data-ttu-id="e8bfc-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8bfc-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e8bfc-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8bfc-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e8bfc-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e8bfc-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
