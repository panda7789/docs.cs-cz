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
ms.openlocfilehash: 5d8827f46a12bd090fa27e71072d833607d34677
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777359"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="8e079-102">EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="8e079-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="8e079-103">Načte vlastní atributy na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e079-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e079-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e079-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e079-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e079-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8e079-106">Popisovač čítače.</span><span class="sxs-lookup"><span data-stu-id="8e079-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="8e079-107">Typ atributů, které mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="8e079-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="8e079-108">Použijte `mdTokenNill` pro všechny atributy.</span><span class="sxs-lookup"><span data-stu-id="8e079-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="8e079-109">Přijímá vlastní tokeny atributů.</span><span class="sxs-lookup"><span data-stu-id="8e079-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8e079-110">Určuje velikost `rCustomValues` pole.</span><span class="sxs-lookup"><span data-stu-id="8e079-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="8e079-111">Volitelně přijímá počet hodnot tokenu.</span><span class="sxs-lookup"><span data-stu-id="8e079-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e079-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8e079-112">Return Value</span></span>  
 <span data-ttu-id="8e079-113">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8e079-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e079-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e079-114">Requirements</span></span>  
 <span data-ttu-id="8e079-115">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="8e079-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e079-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e079-116">See also</span></span>

- [<span data-ttu-id="8e079-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e079-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8e079-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e079-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8e079-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8e079-119">ALink API</span></span>](index.md)
