---
title: '&#39;Volitelné&#39; očekávání'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 52e4288255a246f78730b33beb55f6d2d83ff214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593951"
---
# <a name="39optional39-expected"></a><span data-ttu-id="ceb76-102">&#39;Volitelné&#39; očekávání</span><span class="sxs-lookup"><span data-stu-id="ceb76-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="ceb76-103">Požadovaný argument následuje za volitelným argumentem v deklaraci postupu.</span><span class="sxs-lookup"><span data-stu-id="ceb76-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="ceb76-104">Každý argument za volitelným argumentem musí být také volitelné.</span><span class="sxs-lookup"><span data-stu-id="ceb76-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="ceb76-105">**ID chyby:** BC30202</span><span class="sxs-lookup"><span data-stu-id="ceb76-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ceb76-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ceb76-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="ceb76-107">Pokud je argument bude vyžadovat, přesuňte jej na atributy stála před první nepovinný argument v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="ceb76-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="ceb76-108">Pokud argument má být volitelné, použijte `Optional` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ceb76-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb76-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ceb76-109">See Also</span></span>  
 [<span data-ttu-id="ceb76-110">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="ceb76-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
