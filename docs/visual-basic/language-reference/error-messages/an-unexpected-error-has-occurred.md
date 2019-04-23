---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9aa7ba0babe0a89942e320a76e07c05162b31700
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313604"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="69160-102">Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.</span><span class="sxs-lookup"><span data-stu-id="69160-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="69160-103">Aplikaci nebylo možné získat prostředek operačního systému nutné.</span><span class="sxs-lookup"><span data-stu-id="69160-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="69160-104">Zde jsou některé možné příčiny tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="69160-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="69160-105">Aplikace nemá oprávnění k vytvoření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="69160-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="69160-106">Modul common language runtime nemá oprávnění k vytvoření souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="69160-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="69160-107">Aplikace potřebuje pro přístup k objektu operačního systému, ale používá jiný proces.</span><span class="sxs-lookup"><span data-stu-id="69160-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69160-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="69160-108">To correct this error</span></span>  
  
1. <span data-ttu-id="69160-109">Zkontrolujte, zda má dostatečná oprávnění k vytvoření aplikace s názvem objekty operačního systému.</span><span class="sxs-lookup"><span data-stu-id="69160-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="69160-110">Zkontrolujte, zda modul common language runtime má dostatečná oprávnění k vytvoření souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="69160-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="69160-111">Restartujte počítač a zrušte všechny procesy, které mohou být zdroje potřebné pro připojení k původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="69160-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="69160-112">Všimněte si okolnosti, kdy došlo k chybě a volat Microsoft Product Support Services</span><span class="sxs-lookup"><span data-stu-id="69160-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69160-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69160-113">See also</span></span>

- [<span data-ttu-id="69160-114">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69160-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="69160-115">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="69160-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="69160-116">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="69160-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
