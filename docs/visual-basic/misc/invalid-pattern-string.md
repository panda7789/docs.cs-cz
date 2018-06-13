---
title: Neplatný vzor řetězce
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4905f74683989d8e1a2b041a8af4af4d7432ffab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33635642"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="73522-102">Neplatný vzor řetězce</span><span class="sxs-lookup"><span data-stu-id="73522-102">Invalid pattern string</span></span>
<span data-ttu-id="73522-103">Vzor řetězec zadaný v poli `Like` operace hledání je neplatný.</span><span class="sxs-lookup"><span data-stu-id="73522-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73522-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="73522-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="73522-105">Zkontrolujte platné znaky pro seznam výrazů.</span><span class="sxs-lookup"><span data-stu-id="73522-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="73522-106">V rozsahu vzor, zajistěte, aby byl znak spuštění rozsah menší než koncový rozsah znak, jako v `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="73522-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="73522-107">V rozsahu vzor, ujistěte se, že nejsou k dispozici více pomlčky vedle sebe, jako v `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="73522-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="73522-108">Ukončení vzor oblastí s pravá závorka.</span><span class="sxs-lookup"><span data-stu-id="73522-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73522-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="73522-109">See Also</span></span>  
 [<span data-ttu-id="73522-110">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="73522-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
