---
title: Byla očekávána deklarace.
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: c5c9b665b78c7c63c55292e38cc96ee8b2962a61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583887"
---
# <a name="declaration-expected"></a><span data-ttu-id="d9f20-102">Byla očekávána deklarace.</span><span class="sxs-lookup"><span data-stu-id="d9f20-102">Declaration expected</span></span>
<span data-ttu-id="d9f20-103">Výpis nondeclarative, jako je například přiřazení nebo smyčky příkaz proběhne mimo všechny postupu.</span><span class="sxs-lookup"><span data-stu-id="d9f20-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="d9f20-104">Mimo postupy jsou povoleny pouze deklarace.</span><span class="sxs-lookup"><span data-stu-id="d9f20-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="d9f20-105">Alternativně programovací element je deklarovaná bez klíčového slova deklarace, jako `Dim` nebo `Const`.</span><span class="sxs-lookup"><span data-stu-id="d9f20-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="d9f20-106">**ID chyby:** BC30188</span><span class="sxs-lookup"><span data-stu-id="d9f20-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9f20-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d9f20-107">To correct this error</span></span>  
  
-   <span data-ttu-id="d9f20-108">Příkaz nondeclarative přesunete k tělu procedury.</span><span class="sxs-lookup"><span data-stu-id="d9f20-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
-   <span data-ttu-id="d9f20-109">Zahájit deklarace s – klíčové slovo odpovídající deklarace.</span><span class="sxs-lookup"><span data-stu-id="d9f20-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
-   <span data-ttu-id="d9f20-110">Ujistěte se, že není zadáno chybně deklarace klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d9f20-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f20-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9f20-111">See Also</span></span>  
 [<span data-ttu-id="d9f20-112">Procedury</span><span class="sxs-lookup"><span data-stu-id="d9f20-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="d9f20-113">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="d9f20-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
