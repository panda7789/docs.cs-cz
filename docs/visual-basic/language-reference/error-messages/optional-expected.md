---
title: '&#39;Volitelné&#39; očekávání'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 46bd84e2bcf5c5bea11a5c9d8b6e9254c49e3021
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642474"
---
# <a name="39optional39-expected"></a><span data-ttu-id="0d40d-102">&#39;Volitelné&#39; očekávání</span><span class="sxs-lookup"><span data-stu-id="0d40d-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="0d40d-103">Volitelný argument v deklaraci procedury následuje povinný argument.</span><span class="sxs-lookup"><span data-stu-id="0d40d-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="0d40d-104">Každý argument volitelným argumentem musí být také volitelný.</span><span class="sxs-lookup"><span data-stu-id="0d40d-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="0d40d-105">**ID chyby:** BC30202</span><span class="sxs-lookup"><span data-stu-id="0d40d-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0d40d-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0d40d-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="0d40d-107">Pokud má být povinný argument, přesuňte ho před první nepovinný argument v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="0d40d-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="0d40d-108">Pokud má být volitelný argument, použijte `Optional` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0d40d-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d40d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d40d-109">See also</span></span>
- [<span data-ttu-id="0d40d-110">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="0d40d-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
