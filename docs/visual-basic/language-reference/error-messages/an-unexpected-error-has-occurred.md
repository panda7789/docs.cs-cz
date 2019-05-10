---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 8130eee93ab5c14043283c28f522da53f9047e85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646888"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="3c6d8-102">Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="3c6d8-103">Aplikaci nebylo možné získat prostředek operačního systému nutné.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="3c6d8-104">Zde jsou některé možné příčiny tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="3c6d8-104">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="3c6d8-105">Aplikace nemá oprávnění k vytvoření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="3c6d8-106">Modul common language runtime nemá oprávnění k vytvoření souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="3c6d8-107">Aplikace potřebuje pro přístup k objektu operačního systému, ale používá jiný proces.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c6d8-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3c6d8-108">To correct this error</span></span>  
  
1. <span data-ttu-id="3c6d8-109">Zkontrolujte, zda má dostatečná oprávnění k vytvoření aplikace s názvem objekty operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="3c6d8-110">Zkontrolujte, zda modul common language runtime má dostatečná oprávnění k vytvoření souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="3c6d8-111">Restartujte počítač a zrušte všechny procesy, které mohou být zdroje potřebné pro připojení k původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c6d8-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="3c6d8-112">Všimněte si okolnosti, kdy došlo k chybě a volat Microsoft Product Support Services</span><span class="sxs-lookup"><span data-stu-id="3c6d8-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6d8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c6d8-113">See also</span></span>

- [<span data-ttu-id="3c6d8-114">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c6d8-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="3c6d8-115">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="3c6d8-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="3c6d8-116">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="3c6d8-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
