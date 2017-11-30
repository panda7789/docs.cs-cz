---
title: "Neplatný vzor řetězce"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="069d7-102">Neplatný vzor řetězce</span><span class="sxs-lookup"><span data-stu-id="069d7-102">Invalid pattern string</span></span>
<span data-ttu-id="069d7-103">Vzor řetězec zadaný v poli `Like` operace hledání je neplatný.</span><span class="sxs-lookup"><span data-stu-id="069d7-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="069d7-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="069d7-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="069d7-105">Zkontrolujte platné znaky pro seznam výrazů.</span><span class="sxs-lookup"><span data-stu-id="069d7-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="069d7-106">V rozsahu vzor, zajistěte, aby byl znak spuštění rozsah menší než koncový rozsah znak, jako v `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="069d7-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="069d7-107">V rozsahu vzor, ujistěte se, že nejsou k dispozici více pomlčky vedle sebe, jako v `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="069d7-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="069d7-108">Ukončení vzor oblastí s pravá závorka.</span><span class="sxs-lookup"><span data-stu-id="069d7-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069d7-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="069d7-109">See Also</span></span>  
 [<span data-ttu-id="069d7-110">Like – operátor</span><span class="sxs-lookup"><span data-stu-id="069d7-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
