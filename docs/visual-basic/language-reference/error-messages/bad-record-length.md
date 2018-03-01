---
title: "Chybná délka záznamu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-record-length"></a><span data-ttu-id="48dc6-102">Chybná délka záznamu</span><span class="sxs-lookup"><span data-stu-id="48dc6-102">Bad record length</span></span>
<span data-ttu-id="48dc6-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="48dc6-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="48dc6-104">Délka zadaná v proměnné záznam `FileGet`, `FileGetObject`, `FilePut` nebo `FilePutObject` příkazu se liší od délka zadaná v odpovídající `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="48dc6-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="48dc6-105">Proměnné v `FilePut` nebo `FilePutObject` příkaz není nebo obsahuje řetězec s proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="48dc6-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="48dc6-106">Proměnné v `FilePut` nebo `FilePutObject` zahrnuje nebo je `Variant` typu.</span><span class="sxs-lookup"><span data-stu-id="48dc6-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="48dc6-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="48dc6-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="48dc6-108">Zajistěte, aby součet hodnot velikosti pevnou délkou proměnné v uživatelsky definovaný typ. typ záznamu proměnnou definujete je stejný jako hodnota uvedená v `FileOpen` na příkaz `Len` klauzule.</span><span class="sxs-lookup"><span data-stu-id="48dc6-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="48dc6-109">Pokud proměnné v `FilePut` nebo `FilePutObject` příkaz nebo obsahuje řetězec s proměnnou délkou, zkontrolujte, zda řetězec proměnné délky je kratší než délka záznamu zadaný v aspoň 2 znaky `Len` klauzuli `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="48dc6-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="48dc6-110">Pokud proměnné v `FilePut` nebo `FilePutObject` zahrnuje nebo je `Variant` zkontrolujte, zda řetězec proměnné délky je kratší než délka záznamu zadaný v minimálně 4 bajtů `Len` klauzuli `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="48dc6-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48dc6-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="48dc6-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
