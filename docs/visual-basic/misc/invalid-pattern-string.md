---
title: Neplatný řetězec vzoru.
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: bc2e91060ca1b0e21ea28b0f08febc3e0c54f4f1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58027317"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="ac2d6-102">Neplatný řetězec vzoru.</span><span class="sxs-lookup"><span data-stu-id="ac2d6-102">Invalid pattern string</span></span>
<span data-ttu-id="ac2d6-103">Vzor řetězec zadaný v poli `Like` operace hledání je neplatná.</span><span class="sxs-lookup"><span data-stu-id="ac2d6-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ac2d6-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ac2d6-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="ac2d6-105">Projděte si platné znaky pro seznam výrazů.</span><span class="sxs-lookup"><span data-stu-id="ac2d6-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="ac2d6-106">V rozsahu vzor, ujistěte se, že znak počáteční rozsah menší než koncový rozsah znaků, stejně jako v `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="ac2d6-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="ac2d6-107">V rozsahu vzor, zajistěte, aby nebyl více pomlčky vedle sebe, stejně jako v `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="ac2d6-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="ac2d6-108">Koncový rozsahů vzor s pravou hranatou závorku.</span><span class="sxs-lookup"><span data-stu-id="ac2d6-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2d6-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac2d6-109">See also</span></span>

- [<span data-ttu-id="ac2d6-110">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="ac2d6-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
