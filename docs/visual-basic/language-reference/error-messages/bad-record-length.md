---
title: Chybná délka záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 37d9da67656ec4821903d8ba67a27ef10f1a437d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728858"
---
# <a name="bad-record-length"></a><span data-ttu-id="d13a6-102">Chybná délka záznamu</span><span class="sxs-lookup"><span data-stu-id="d13a6-102">Bad record length</span></span>
<span data-ttu-id="d13a6-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="d13a6-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="d13a6-104">Délka záznamu proměnná, zadaný v `FileGet`, `FileGetObject`, `FilePut` nebo `FilePutObject` příkazu se liší od délka zadaná v odpovídající `FileOpen` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d13a6-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="d13a6-105">Proměnné v `FilePut` nebo `FilePutObject` je příkaz nebo obsahuje řetězec s proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="d13a6-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="d13a6-106">Proměnné v `FilePut` nebo `FilePutObject` je nebo zahrnuje `Variant` typu.</span><span class="sxs-lookup"><span data-stu-id="d13a6-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d13a6-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d13a6-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="d13a6-108">Ujistěte se, že součet velikostí proměnné pevné délky v uživatelem definovaný typ definuje typ záznamu proměnná je stejná jako hodnota uvedená v `FileOpen` příkazu `Len` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d13a6-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="d13a6-109">Pokud proměnnou v `FilePut` nebo `FilePutObject` příkazu nebo obsahuje řetězec s proměnnou délkou, ujistěte se, že je kratší než délka záznamu určená v aspoň 2 znaky řetězce proměnné délky `Len` klauzuli `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d13a6-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="d13a6-110">Pokud proměnné v `FilePut` nebo `FilePutObject` není nebo obsahuje `Variant` Ujistěte se, že řetězce proměnné délky je kratší než délka záznamu určená v alespoň 4 bajty `Len` klauzuli `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d13a6-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13a6-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d13a6-111">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
