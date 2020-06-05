---
title: Byla očekávána deklarace.
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 237622d0dc6c57f66d402f491a6191a5911574e2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409735"
---
# <a name="declaration-expected"></a><span data-ttu-id="76788-102">Byla očekávána deklarace.</span><span class="sxs-lookup"><span data-stu-id="76788-102">Declaration expected</span></span>
<span data-ttu-id="76788-103">Nedeklarativní příkaz, jako je například přiřazení nebo příkaz LOOP, se vyskytuje mimo jakoukoli proceduru.</span><span class="sxs-lookup"><span data-stu-id="76788-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="76788-104">Mimo procedury jsou povoleny pouze deklarace.</span><span class="sxs-lookup"><span data-stu-id="76788-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="76788-105">Alternativně je programovací prvek deklarován bez klíčového slova deklarace, jako je například `Dim` nebo `Const` .</span><span class="sxs-lookup"><span data-stu-id="76788-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="76788-106">**ID chyby:** BC30188</span><span class="sxs-lookup"><span data-stu-id="76788-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="76788-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="76788-107">To correct this error</span></span>  
  
- <span data-ttu-id="76788-108">Přesuňte nedeklarativní příkaz do těla procedury.</span><span class="sxs-lookup"><span data-stu-id="76788-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
- <span data-ttu-id="76788-109">Spusťte deklaraci s příslušným klíčovým slovem deklarace.</span><span class="sxs-lookup"><span data-stu-id="76788-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
- <span data-ttu-id="76788-110">Zajistěte, aby klíčové slovo deklarace nebylo špatně napsané.</span><span class="sxs-lookup"><span data-stu-id="76788-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76788-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="76788-111">See also</span></span>

- [<span data-ttu-id="76788-112">Procedury</span><span class="sxs-lookup"><span data-stu-id="76788-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="76788-113">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="76788-113">Dim Statement</span></span>](../statements/dim-statement.md)
