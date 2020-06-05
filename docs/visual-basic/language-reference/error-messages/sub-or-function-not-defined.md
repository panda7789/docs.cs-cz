---
title: Příkaz Sub nebo funkce nejsou definované.
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 9eb13d943f9f1cffc984847f7339111e06f5aa6b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373924"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="9c231-102">Příkaz Sub nebo funkce není definována (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c231-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="9c231-103">`Sub` `Function` Musí být definován, aby mohl být volán.</span><span class="sxs-lookup"><span data-stu-id="9c231-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="9c231-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="9c231-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="9c231-105">Název procedury je chybný.</span><span class="sxs-lookup"><span data-stu-id="9c231-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="9c231-106">Pokus o volání procedury z jiného projektu, aniž by bylo nutné explicitně přidat odkaz na tento projekt v dialogovém okně **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="9c231-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="9c231-107">Určení procedury, která není viditelná pro volající proceduru.</span><span class="sxs-lookup"><span data-stu-id="9c231-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="9c231-108">Deklarace rutiny DLL (Dynamic-Link Library) systému Windows nebo rutiny kódu systému Macintosh, která není v určeném prostředku knihovny nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="9c231-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c231-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9c231-109">To correct this error</span></span>  
  
1. <span data-ttu-id="9c231-110">Ujistěte se, že je název procedury zadán správně.</span><span class="sxs-lookup"><span data-stu-id="9c231-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="9c231-111">Vyhledejte název projektu, který obsahuje proceduru, kterou chcete volat, v dialogovém okně **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="9c231-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="9c231-112">Pokud se nezobrazí, klikněte na tlačítko **Procházet** a vyhledejte ho.</span><span class="sxs-lookup"><span data-stu-id="9c231-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="9c231-113">Zaškrtněte políčko nalevo od názvu projektu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c231-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="9c231-114">Kontrola názvu rutiny.</span><span class="sxs-lookup"><span data-stu-id="9c231-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c231-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c231-115">See also</span></span>

- [<span data-ttu-id="9c231-116">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="9c231-116">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9c231-117">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="9c231-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="9c231-118">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="9c231-118">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="9c231-119">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="9c231-119">Function Statement</span></span>](../statements/function-statement.md)
