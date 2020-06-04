---
title: Neplatný řetězec vzoru
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402210"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="a28dd-102">Neplatný řetězec vzoru</span><span class="sxs-lookup"><span data-stu-id="a28dd-102">Invalid pattern string</span></span>
<span data-ttu-id="a28dd-103">Řetězec vzorku zadaný v `Like` operaci hledání je neplatný.</span><span class="sxs-lookup"><span data-stu-id="a28dd-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a28dd-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a28dd-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a28dd-105">Zkontrolujte platné znaky pro seznam výrazů.</span><span class="sxs-lookup"><span data-stu-id="a28dd-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="a28dd-106">V rozsahu vzorku zajistěte, aby byl znak začátku rozsahu menší než znak koncového rozsahu, jako v `[a-z]` .</span><span class="sxs-lookup"><span data-stu-id="a28dd-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="a28dd-107">V rozsahu vzorů zajistěte, aby vedle sebe nebyla více spojovníků, jako v `[a--z]` .</span><span class="sxs-lookup"><span data-stu-id="a28dd-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="a28dd-108">Ukončit rozsahy vzorů s pravou závorkou</span><span class="sxs-lookup"><span data-stu-id="a28dd-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28dd-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a28dd-109">See also</span></span>

- [<span data-ttu-id="a28dd-110">Like – operátor</span><span class="sxs-lookup"><span data-stu-id="a28dd-110">Like Operator</span></span>](../language-reference/operators/like-operator.md)
