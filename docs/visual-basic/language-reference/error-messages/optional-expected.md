---
title: Bylo očekáváno klíčové slovo 'Optional'.
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 411e3248409ab0184666f4efefb4ec4becf7cab1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409345"
---
# <a name="optional-expected"></a><span data-ttu-id="c4e4d-102">Bylo očekáváno klíčové slovo 'Optional'.</span><span class="sxs-lookup"><span data-stu-id="c4e4d-102">'Optional' expected</span></span>
<span data-ttu-id="c4e4d-103">Volitelný argument deklarace procedury je následován povinným argumentem.</span><span class="sxs-lookup"><span data-stu-id="c4e4d-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="c4e4d-104">Každý argument následující po volitelném argumentu musí být také volitelný.</span><span class="sxs-lookup"><span data-stu-id="c4e4d-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="c4e4d-105">**ID chyby:** BC30202</span><span class="sxs-lookup"><span data-stu-id="c4e4d-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4e4d-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c4e4d-106">To correct this error</span></span>  
  
1. <span data-ttu-id="c4e4d-107">Pokud má být argument požadován, přesuňte jej před první volitelný argument v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="c4e4d-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="c4e4d-108">Pokud argument má být nepovinný, použijte `Optional` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c4e4d-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e4d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4e4d-109">See also</span></span>

- [<span data-ttu-id="c4e4d-110">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="c4e4d-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
