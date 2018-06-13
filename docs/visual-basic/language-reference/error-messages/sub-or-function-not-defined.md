---
title: Příkaz Sub nebo funkce není definována (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 58e90d769d5a7f2d88b5c27d1ec7d0d28c8d7b03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593698"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="e15bb-102">Příkaz Sub nebo funkce není definována (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e15bb-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="e15bb-103">A `Sub` nebo `Function` musí být definován, aby bylo možné volat.</span><span class="sxs-lookup"><span data-stu-id="e15bb-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="e15bb-104">Možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="e15bb-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="e15bb-105">Chyba v pravopisu název procedury.</span><span class="sxs-lookup"><span data-stu-id="e15bb-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="e15bb-106">Při pokusu o volání procedury z jiného projektu bez explicitně přidat odkaz na tohoto projektu v **odkazy** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e15bb-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="e15bb-107">Zadání procedury, která není viditelná pro volání procedury.</span><span class="sxs-lookup"><span data-stu-id="e15bb-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="e15bb-108">Deklarování Windows dynamická knihovna (DLL) rutina nebo rutiny Macintosh kód prostředků, který není v zadaný prostředek knihovny nebo kód.</span><span class="sxs-lookup"><span data-stu-id="e15bb-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e15bb-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e15bb-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="e15bb-110">Ujistěte se, že název postupu je napsán správně.</span><span class="sxs-lookup"><span data-stu-id="e15bb-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="e15bb-111">Najít název projektu, který obsahuje postup, který chcete použít **odkazy** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e15bb-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="e15bb-112">Pokud se nezobrazí, klikněte **Procházet** tlačítko ji najít.</span><span class="sxs-lookup"><span data-stu-id="e15bb-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="e15bb-113">Zaškrtněte políčko nalevo od názvu projektu a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="e15bb-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e15bb-114">Zkontrolujte název rutiny.</span><span class="sxs-lookup"><span data-stu-id="e15bb-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15bb-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e15bb-115">See Also</span></span>  
 [<span data-ttu-id="e15bb-116">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="e15bb-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="e15bb-117">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="e15bb-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="e15bb-118">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="e15bb-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="e15bb-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="e15bb-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
