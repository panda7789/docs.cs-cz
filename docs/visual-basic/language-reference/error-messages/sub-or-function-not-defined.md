---
title: Příkaz Sub nebo funkce nejsou definované.
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 8b81460eccb6be8baa2ea7bc68d0f80c9d16398e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349579"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="da9fa-102">Příkaz Sub nebo funkce není definována (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da9fa-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="da9fa-103">Aby bylo možné volat `Sub`, musí být definován nebo `Function`.</span><span class="sxs-lookup"><span data-stu-id="da9fa-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="da9fa-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="da9fa-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="da9fa-105">Název procedury je chybný.</span><span class="sxs-lookup"><span data-stu-id="da9fa-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="da9fa-106">Pokus o volání procedury z jiného projektu, aniž by bylo nutné explicitně přidat odkaz na tento projekt v dialogovém okně **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="da9fa-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="da9fa-107">Určení procedury, která není viditelná pro volající proceduru.</span><span class="sxs-lookup"><span data-stu-id="da9fa-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="da9fa-108">Deklarace rutiny DLL (Dynamic-Link Library) systému Windows nebo rutiny kódu systému Macintosh, která není v určeném prostředku knihovny nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="da9fa-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da9fa-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="da9fa-109">To correct this error</span></span>  
  
1. <span data-ttu-id="da9fa-110">Ujistěte se, že je název procedury zadán správně.</span><span class="sxs-lookup"><span data-stu-id="da9fa-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="da9fa-111">Vyhledejte název projektu, který obsahuje proceduru, kterou chcete volat, v dialogovém okně **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="da9fa-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="da9fa-112">Pokud se nezobrazí, klikněte na tlačítko **Procházet** a vyhledejte ho.</span><span class="sxs-lookup"><span data-stu-id="da9fa-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="da9fa-113">Zaškrtněte políčko nalevo od názvu projektu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="da9fa-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="da9fa-114">Kontrola názvu rutiny.</span><span class="sxs-lookup"><span data-stu-id="da9fa-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9fa-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da9fa-115">See also</span></span>

- [<span data-ttu-id="da9fa-116">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="da9fa-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="da9fa-117">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="da9fa-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="da9fa-118">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="da9fa-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="da9fa-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="da9fa-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
