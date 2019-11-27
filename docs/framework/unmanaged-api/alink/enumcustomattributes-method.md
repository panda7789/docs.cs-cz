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
ms.openlocfilehash: 6a5b3f1e9bf1444feb73949ef7133fbd9ae35134
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446469"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="e6aaa-102">EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="e6aaa-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="e6aaa-103">Načte vlastní atributy na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6aaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6aaa-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6aaa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6aaa-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e6aaa-106">Popisovač čítače.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="e6aaa-107">Typ atributů, které mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="e6aaa-108">Pro všechny atributy použijte `mdTokenNill`.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="e6aaa-109">Přijímá vlastní tokeny atributů.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e6aaa-110">Určuje velikost `rCustomValues` pole.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="e6aaa-111">Volitelně přijímá počet hodnot tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6aaa-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e6aaa-112">Return Value</span></span>  
 <span data-ttu-id="e6aaa-113">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e6aaa-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6aaa-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6aaa-114">Requirements</span></span>  
 <span data-ttu-id="e6aaa-115">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="e6aaa-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6aaa-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6aaa-116">See also</span></span>

- [<span data-ttu-id="e6aaa-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6aaa-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e6aaa-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6aaa-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e6aaa-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e6aaa-119">ALink API</span></span>](index.md)
