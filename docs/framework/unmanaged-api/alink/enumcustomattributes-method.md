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
ms.openlocfilehash: 09ccf731f0494b6eda49f6a15d04970a723c473b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742054"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="43054-102">EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="43054-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="43054-103">Načte vlastní atributy úrovně sestavení.</span><span class="sxs-lookup"><span data-stu-id="43054-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43054-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43054-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="43054-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43054-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="43054-106">Popisovač výčtu.</span><span class="sxs-lookup"><span data-stu-id="43054-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="43054-107">Typ atributů, které chcete vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="43054-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="43054-108">Použití `mdTokenNill` pro všechny atributy.</span><span class="sxs-lookup"><span data-stu-id="43054-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="43054-109">Přijímá tokeny vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="43054-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="43054-110">Určuje velikost `rCustomValues` pole.</span><span class="sxs-lookup"><span data-stu-id="43054-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="43054-111">Volitelně přijímá počet hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="43054-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43054-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="43054-112">Return Value</span></span>  
 <span data-ttu-id="43054-113">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="43054-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43054-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43054-114">Requirements</span></span>  
 <span data-ttu-id="43054-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="43054-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43054-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43054-116">See also</span></span>

- [<span data-ttu-id="43054-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43054-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="43054-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43054-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="43054-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="43054-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
