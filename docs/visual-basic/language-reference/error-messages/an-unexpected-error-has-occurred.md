---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="f956b-102">Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.</span><span class="sxs-lookup"><span data-stu-id="f956b-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="f956b-103">Aplikace se nedá získat prostředek nezbytné operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f956b-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="f956b-104">Jsou některé možné příčiny tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="f956b-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="f956b-105">Aplikace nemá oprávnění k vytvoření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f956b-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="f956b-106">Modul common language runtime nemá oprávnění k vytvoření soubory mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="f956b-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="f956b-107">Aplikace potřebuje přístup k objektu operačního systému, ale jej používá jiný proces.</span><span class="sxs-lookup"><span data-stu-id="f956b-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f956b-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f956b-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="f956b-109">Zkontrolujte, že aplikace má dostatečná oprávnění k vytvoření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f956b-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="f956b-110">Zkontrolujte, zda modul common language runtime má dostatečná oprávnění k vytvoření soubory mapované paměti.</span><span class="sxs-lookup"><span data-stu-id="f956b-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="f956b-111">Restartujte počítač zrušte všechny procesy, které může být prostředků potřebné pro připojení k původní instance aplikace.</span><span class="sxs-lookup"><span data-stu-id="f956b-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="f956b-112">Poznámka: v případech, za kterých se stala chyba a volání služby Microsoft Product Support Services</span><span class="sxs-lookup"><span data-stu-id="f956b-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f956b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f956b-113">See Also</span></span>  
 [<span data-ttu-id="f956b-114">Stránka aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f956b-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="f956b-115">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="f956b-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="f956b-116">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="f956b-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
