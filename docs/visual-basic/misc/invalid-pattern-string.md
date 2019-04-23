---
title: Neplatný řetězec vzoru.
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298679"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="f37fb-102">Neplatný řetězec vzoru.</span><span class="sxs-lookup"><span data-stu-id="f37fb-102">Invalid pattern string</span></span>
<span data-ttu-id="f37fb-103">Vzor řetězec zadaný v poli `Like` operace hledání je neplatná.</span><span class="sxs-lookup"><span data-stu-id="f37fb-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f37fb-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f37fb-104">To correct this error</span></span>  
  
1. <span data-ttu-id="f37fb-105">Projděte si platné znaky pro seznam výrazů.</span><span class="sxs-lookup"><span data-stu-id="f37fb-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="f37fb-106">V rozsahu vzor, ujistěte se, že znak počáteční rozsah menší než koncový rozsah znaků, stejně jako v `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="f37fb-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="f37fb-107">V rozsahu vzor, zajistěte, aby nebyl více pomlčky vedle sebe, stejně jako v `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="f37fb-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="f37fb-108">Koncový rozsahů vzor s pravou hranatou závorku.</span><span class="sxs-lookup"><span data-stu-id="f37fb-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37fb-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f37fb-109">See also</span></span>

- [<span data-ttu-id="f37fb-110">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="f37fb-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
