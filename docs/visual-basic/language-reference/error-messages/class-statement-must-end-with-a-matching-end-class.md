---
title: '&#39;Třída&#39; příkaz musí být ukončen párovým klíčovým &#39;End Class&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 4e80ce58048bfa7f2fecc65e7167479df07bf57c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715085"
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="7c4e0-102">&#39;Třída&#39; příkaz musí být ukončen párovým klíčovým &#39;End Class&#39;</span><span class="sxs-lookup"><span data-stu-id="7c4e0-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="7c4e0-103">`Class` slouží k zahájení `Class` blokovat; proto se může vyskytovat jenom na začátku bloku k odpovídajícímu `End Class` příkaz koncový blok.</span><span class="sxs-lookup"><span data-stu-id="7c4e0-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="7c4e0-104">Máte buď redundantní `Class` příkazu, nebo nebyly skončilo vaše `Class` blokovat s `End Class`.</span><span class="sxs-lookup"><span data-stu-id="7c4e0-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="7c4e0-105">**ID chyby:** BC30481</span><span class="sxs-lookup"><span data-stu-id="7c4e0-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7c4e0-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7c4e0-106">To correct this error</span></span>  
  
-   <span data-ttu-id="7c4e0-107">Vyhledat a odebrat nadbytečné `Class` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7c4e0-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="7c4e0-108">Uzavřít `Class` bloku k odpovídajícímu `End Class`.</span><span class="sxs-lookup"><span data-stu-id="7c4e0-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4e0-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c4e0-109">See also</span></span>
- [<span data-ttu-id="7c4e0-110">End \<– klíčové slovo > – příkaz</span><span class="sxs-lookup"><span data-stu-id="7c4e0-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [<span data-ttu-id="7c4e0-111">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="7c4e0-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
