---
title: Příkaz Sub nebo funkce není definována (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 397648618ea3764efafb5cff41deaef320bbeff3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982433"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="8ae70-102">Příkaz Sub nebo funkce není definována (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ae70-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="8ae70-103">A `Sub` nebo `Function` musí být definován, aby bylo možné volat.</span><span class="sxs-lookup"><span data-stu-id="8ae70-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="8ae70-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="8ae70-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="8ae70-105">Chyba v pravopisu název procedury.</span><span class="sxs-lookup"><span data-stu-id="8ae70-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="8ae70-106">Při pokusu o volání procedury z jiného projektu bez nutnosti explicitně přidávat odkaz na tento projekt v **odkazy** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="8ae70-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="8ae70-107">Určení procedury, která není viditelná pro volání procedury.</span><span class="sxs-lookup"><span data-stu-id="8ae70-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="8ae70-108">Deklarování rutiny Windows dynamická knihovna (DLL) nebo Macintosh kód prostředků rutiny, která není v zadané zdroje knihovny nebo kód.</span><span class="sxs-lookup"><span data-stu-id="8ae70-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ae70-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8ae70-109">To correct this error</span></span>  
  
1. <span data-ttu-id="8ae70-110">Ujistěte se, jestli název procedury je napsaný správně.</span><span class="sxs-lookup"><span data-stu-id="8ae70-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="8ae70-111">Vyhledání názvu projektu, který obsahuje postup, chcete volat **odkazy** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="8ae70-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="8ae70-112">Pokud se nezobrazí, klikněte na tlačítko **Procházet** tlačítko ji najít.</span><span class="sxs-lookup"><span data-stu-id="8ae70-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="8ae70-113">Zaškrtněte políčko nalevo od názvu projektu a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ae70-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="8ae70-114">Zkontrolujte název rutiny.</span><span class="sxs-lookup"><span data-stu-id="8ae70-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae70-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ae70-115">See also</span></span>

- [<span data-ttu-id="8ae70-116">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="8ae70-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="8ae70-117">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="8ae70-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="8ae70-118">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="8ae70-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="8ae70-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="8ae70-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
