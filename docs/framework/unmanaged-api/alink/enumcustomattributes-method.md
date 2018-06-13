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
ms.openlocfilehash: 5a3d7d3bb05a878f4d9832cf39a8e8863929c4e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403211"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="8b9b8-102">EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="8b9b8-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="8b9b8-103">Načte vlastní atributy úrovně sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b9b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b9b8-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b9b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b9b8-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8b9b8-106">Popisovač výčtu.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="8b9b8-107">Typ atributů, které chcete vytvořit její výčet.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="8b9b8-108">Použití `mdTokenNill` pro všechny atributy.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="8b9b8-109">Přijímá tokeny vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8b9b8-110">Určuje velikost `rCustomValues` pole.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="8b9b8-111">Volitelně obdrží počet hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b9b8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8b9b8-112">Return Value</span></span>  
 <span data-ttu-id="8b9b8-113">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8b9b8-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b9b8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b9b8-114">Requirements</span></span>  
 <span data-ttu-id="8b9b8-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="8b9b8-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b9b8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b9b8-116">See Also</span></span>  
 [<span data-ttu-id="8b9b8-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b9b8-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8b9b8-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b9b8-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8b9b8-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8b9b8-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
