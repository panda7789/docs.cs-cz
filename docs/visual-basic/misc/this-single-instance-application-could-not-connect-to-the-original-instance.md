---
title: Nelze se připojit k původní instanci této aplikace s jedinou instancí
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 7ffa9b185e16cfdf8223ce84e77d1a0e1fa67f65
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322651"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="61910-102">Nelze se připojit k původní instanci této aplikace s jedinou instancí</span><span class="sxs-lookup"><span data-stu-id="61910-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="61910-103">Tato aplikace s jedinou instancí se nemohl připojit k původní instanci.</span><span class="sxs-lookup"><span data-stu-id="61910-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="61910-104">Některé možné příčiny tohoto problému jsou následující:</span><span class="sxs-lookup"><span data-stu-id="61910-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="61910-105">Původní instance přestala reagovat.</span><span class="sxs-lookup"><span data-stu-id="61910-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="61910-106">Aplikace nemá oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="61910-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="61910-107">Další informace o objektech jádra najdete v tématu [mutexů](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="61910-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="61910-108">Základní název pro objekty jádra pochází z zřetězení identifikátor GUID, číslo hlavní verze a vedlejší číslo verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="61910-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="61910-109">Základní název může být například `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="61910-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="61910-110">Chcete-li opravit tuto chybu při vývoji aplikace</span><span class="sxs-lookup"><span data-stu-id="61910-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="61910-111">Zkontrolujte, jestli aplikace nepřešel do nereagujícího stavu.</span><span class="sxs-lookup"><span data-stu-id="61910-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="61910-112">Zkontrolujte, že aplikace má dostatečná oprávnění k vytváření objektů jádra.</span><span class="sxs-lookup"><span data-stu-id="61910-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="61910-113">Restartujte na původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="61910-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="61910-114">Restartujte počítač a zrušte všechny procesy, které může být na prostředek, který se nejde připojit k původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="61910-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="61910-115">Všimněte si okolnosti, kdy došlo k chybě a telefonní Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="61910-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61910-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61910-116">See also</span></span>

- [<span data-ttu-id="61910-117">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="61910-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
