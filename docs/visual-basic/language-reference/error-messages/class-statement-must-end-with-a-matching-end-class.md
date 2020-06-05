---
title: Příkaz 'Class' musí být ukončen odpovídajícím příkazem 'End Class'.
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 01c231f577d21028e9ef92f37c7ac5f7f1fe2aa3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415385"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="58240-102">Příkaz 'Class' musí být ukončen odpovídajícím příkazem 'End Class'.</span><span class="sxs-lookup"><span data-stu-id="58240-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="58240-103">`Class`slouží k inicializaci bloku, `Class` takže se může vyskytovat pouze na začátku bloku s párovým příkazem, který `End Class` ukončuje blok.</span><span class="sxs-lookup"><span data-stu-id="58240-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="58240-104">Buď máte redundantní `Class` příkaz, nebo jste svůj blok neukončili `Class` pomocí `End Class` .</span><span class="sxs-lookup"><span data-stu-id="58240-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="58240-105">**ID chyby:** BC30481</span><span class="sxs-lookup"><span data-stu-id="58240-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58240-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="58240-106">To correct this error</span></span>  
  
- <span data-ttu-id="58240-107">Vyhledejte a odeberte nepotřebný `Class` příkaz.</span><span class="sxs-lookup"><span data-stu-id="58240-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="58240-108">`Class`Uzavřete blok se spárováním `End Class` .</span><span class="sxs-lookup"><span data-stu-id="58240-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58240-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="58240-109">See also</span></span>

- [<span data-ttu-id="58240-110">\<keyword>Příkaz end</span><span class="sxs-lookup"><span data-stu-id="58240-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="58240-111">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="58240-111">Class Statement</span></span>](../statements/class-statement.md)
