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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199138"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="19233-102">EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="19233-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="19233-103">Načte vlastní atributy úrovně sestavení.</span><span class="sxs-lookup"><span data-stu-id="19233-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19233-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19233-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="19233-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19233-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="19233-106">Popisovač výčtu.</span><span class="sxs-lookup"><span data-stu-id="19233-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="19233-107">Typ atributů, které chcete vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="19233-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="19233-108">Použití `mdTokenNill` pro všechny atributy.</span><span class="sxs-lookup"><span data-stu-id="19233-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="19233-109">Přijímá tokeny vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="19233-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="19233-110">Určuje velikost `rCustomValues` pole.</span><span class="sxs-lookup"><span data-stu-id="19233-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="19233-111">Volitelně přijímá počet hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="19233-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19233-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="19233-112">Return Value</span></span>  
 <span data-ttu-id="19233-113">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="19233-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19233-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19233-114">Requirements</span></span>  
 <span data-ttu-id="19233-115">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="19233-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19233-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19233-116">See also</span></span>

- [<span data-ttu-id="19233-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19233-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="19233-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19233-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="19233-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="19233-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
