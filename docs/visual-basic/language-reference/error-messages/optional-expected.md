---
title: Bylo očekáváno klíčové slovo 'Optional'.
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 71a25784f357a7e596093b314ed5b3d721d6f92c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946585"
---
# <a name="optional-expected"></a><span data-ttu-id="db478-102">Bylo očekáváno klíčové slovo 'Optional'.</span><span class="sxs-lookup"><span data-stu-id="db478-102">'Optional' expected</span></span>
<span data-ttu-id="db478-103">Volitelný argument v deklaraci procedury následuje povinný argument.</span><span class="sxs-lookup"><span data-stu-id="db478-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="db478-104">Každý argument volitelným argumentem musí být také volitelný.</span><span class="sxs-lookup"><span data-stu-id="db478-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="db478-105">**ID chyby:** BC30202</span><span class="sxs-lookup"><span data-stu-id="db478-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db478-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="db478-106">To correct this error</span></span>  
  
1. <span data-ttu-id="db478-107">Pokud má být povinný argument, přesuňte ho před první nepovinný argument v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="db478-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="db478-108">Pokud má být volitelný argument, použijte `Optional` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="db478-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db478-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db478-109">See also</span></span>

- [<span data-ttu-id="db478-110">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="db478-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
