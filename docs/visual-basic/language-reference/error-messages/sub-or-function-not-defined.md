---
title: "Příkaz Sub nebo funkce není definována (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="7f97f-102">Příkaz Sub nebo funkce není definována (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f97f-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="7f97f-103">A `Sub` nebo `Function` musí být definován, aby bylo možné volat.</span><span class="sxs-lookup"><span data-stu-id="7f97f-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="7f97f-104">Možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="7f97f-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="7f97f-105">Chyba v pravopisu název procedury.</span><span class="sxs-lookup"><span data-stu-id="7f97f-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="7f97f-106">Při pokusu o volání procedury z jiného projektu bez explicitně přidat odkaz na tohoto projektu v **odkazy** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7f97f-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="7f97f-107">Zadání procedury, která není viditelná pro volání procedury.</span><span class="sxs-lookup"><span data-stu-id="7f97f-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="7f97f-108">Deklarování Windows dynamická knihovna (DLL) rutina nebo rutiny Macintosh kód prostředků, který není v zadaný prostředek knihovny nebo kód.</span><span class="sxs-lookup"><span data-stu-id="7f97f-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7f97f-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7f97f-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="7f97f-110">Ujistěte se, že název postupu je napsán správně.</span><span class="sxs-lookup"><span data-stu-id="7f97f-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="7f97f-111">Najít název projektu, který obsahuje postup, který chcete použít **odkazy** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7f97f-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="7f97f-112">Pokud se nezobrazí, klikněte **Procházet** tlačítko ji najít.</span><span class="sxs-lookup"><span data-stu-id="7f97f-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="7f97f-113">Zaškrtněte políčko nalevo od názvu projektu a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f97f-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="7f97f-114">Zkontrolujte název rutiny.</span><span class="sxs-lookup"><span data-stu-id="7f97f-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f97f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f97f-115">See Also</span></span>  
 [<span data-ttu-id="7f97f-116">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="7f97f-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="7f97f-117">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="7f97f-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="7f97f-118">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="7f97f-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="7f97f-119">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="7f97f-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
