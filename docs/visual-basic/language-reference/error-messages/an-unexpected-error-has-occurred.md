---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 313128d5511ddd0f3b75c58e2c10a74eb967d130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587644"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="62f18-102">Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.</span><span class="sxs-lookup"><span data-stu-id="62f18-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="62f18-103">Aplikace se nedá získat prostředek nezbytné operačního systému.</span><span class="sxs-lookup"><span data-stu-id="62f18-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="62f18-104">Jsou některé možné příčiny tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="62f18-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="62f18-105">Aplikace nemá oprávnění k vytvoření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="62f18-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="62f18-106">Modul common language runtime nemá oprávnění k vytvoření soubory mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="62f18-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="62f18-107">Aplikace potřebuje přístup k objektu operačního systému, ale jej používá jiný proces.</span><span class="sxs-lookup"><span data-stu-id="62f18-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62f18-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="62f18-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="62f18-109">Zkontrolujte, že aplikace má dostatečná oprávnění k vytvoření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="62f18-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="62f18-110">Zkontrolujte, zda modul common language runtime má dostatečná oprávnění k vytvoření soubory mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="62f18-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="62f18-111">Restartujte počítač zrušte všechny procesy, které může být prostředků potřebné pro připojení k původní instance aplikace.</span><span class="sxs-lookup"><span data-stu-id="62f18-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="62f18-112">Poznámka: v případech, za kterých se stala chyba a volání služby Microsoft Product Support Services</span><span class="sxs-lookup"><span data-stu-id="62f18-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f18-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="62f18-113">See Also</span></span>  
 [<span data-ttu-id="62f18-114">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f18-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="62f18-115">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="62f18-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="62f18-116">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="62f18-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
