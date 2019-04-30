---
title: Neplatný řetězec vzoru.
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790595"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="a8f82-102">Neplatný řetězec vzoru.</span><span class="sxs-lookup"><span data-stu-id="a8f82-102">Invalid pattern string</span></span>
<span data-ttu-id="a8f82-103">Vzor řetězec zadaný v poli `Like` operace hledání je neplatná.</span><span class="sxs-lookup"><span data-stu-id="a8f82-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8f82-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a8f82-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a8f82-105">Projděte si platné znaky pro seznam výrazů.</span><span class="sxs-lookup"><span data-stu-id="a8f82-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="a8f82-106">V rozsahu vzor, ujistěte se, že znak počáteční rozsah menší než koncový rozsah znaků, stejně jako v `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="a8f82-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="a8f82-107">V rozsahu vzor, zajistěte, aby nebyl více pomlčky vedle sebe, stejně jako v `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="a8f82-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="a8f82-108">Koncový rozsahů vzor s pravou hranatou závorku.</span><span class="sxs-lookup"><span data-stu-id="a8f82-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f82-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8f82-109">See also</span></span>

- [<span data-ttu-id="a8f82-110">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="a8f82-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
