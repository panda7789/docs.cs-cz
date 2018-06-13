---
title: Chybná délka záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: b4b311e2eb504c485772091ed126b3beb71729cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585967"
---
# <a name="bad-record-length"></a><span data-ttu-id="1032b-102">Chybná délka záznamu</span><span class="sxs-lookup"><span data-stu-id="1032b-102">Bad record length</span></span>
<span data-ttu-id="1032b-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="1032b-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="1032b-104">Délka zadaná v proměnné záznam `FileGet`, `FileGetObject`, `FilePut` nebo `FilePutObject` příkazu se liší od délka zadaná v odpovídající `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1032b-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="1032b-105">Proměnné v `FilePut` nebo `FilePutObject` příkaz není nebo obsahuje řetězec s proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="1032b-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="1032b-106">Proměnné v `FilePut` nebo `FilePutObject` zahrnuje nebo je `Variant` typu.</span><span class="sxs-lookup"><span data-stu-id="1032b-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1032b-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1032b-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="1032b-108">Zajistěte, aby součet hodnot velikosti pevnou délkou proměnné v uživatelsky definovaný typ. typ záznamu proměnnou definujete je stejný jako hodnota uvedená v `FileOpen` na příkaz `Len` klauzule.</span><span class="sxs-lookup"><span data-stu-id="1032b-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="1032b-109">Pokud proměnné v `FilePut` nebo `FilePutObject` příkaz nebo obsahuje řetězec s proměnnou délkou, zkontrolujte, zda řetězec proměnné délky je kratší než délka záznamu zadaný v aspoň 2 znaky `Len` klauzuli `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1032b-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="1032b-110">Pokud proměnné v `FilePut` nebo `FilePutObject` zahrnuje nebo je `Variant` zkontrolujte, zda řetězec proměnné délky je kratší než délka záznamu zadaný v minimálně 4 bajtů `Len` klauzuli `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1032b-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1032b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="1032b-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
