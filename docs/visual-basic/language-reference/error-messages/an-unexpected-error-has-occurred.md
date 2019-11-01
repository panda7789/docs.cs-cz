---
title: Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9643d14b3e94e814c492b362b9db3e37cff4ce9f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197373"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="3d28a-102">Došlo k neočekávané chybě, protože nelze získat prostředek operačního systému požadovaný ke spuštění jedné instance.</span><span class="sxs-lookup"><span data-stu-id="3d28a-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="3d28a-103">Aplikaci se nepovedlo získat potřebný prostředek operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3d28a-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="3d28a-104">Mezi možné příčiny tohoto problému patří:</span><span class="sxs-lookup"><span data-stu-id="3d28a-104">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="3d28a-105">Aplikace nemá oprávnění k vytváření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3d28a-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="3d28a-106">Modul CLR (Common Language Runtime) nemá oprávnění k vytváření souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="3d28a-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="3d28a-107">Aplikace potřebuje přístup k objektu operačního systému, ale používá ho jiný proces.</span><span class="sxs-lookup"><span data-stu-id="3d28a-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3d28a-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3d28a-108">To correct this error</span></span>  
  
1. <span data-ttu-id="3d28a-109">Ověřte, zda má aplikace dostatečná oprávnění k vytváření pojmenovaných objektů operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3d28a-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="3d28a-110">Ověřte, zda má modul common language runtime dostatečná oprávnění k vytváření souborů mapovaných do paměti.</span><span class="sxs-lookup"><span data-stu-id="3d28a-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="3d28a-111">Restartujte počítač a zrušte tak všechny procesy, které mohou používat prostředek potřebný pro připojení k původní instanci aplikace.</span><span class="sxs-lookup"><span data-stu-id="3d28a-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="3d28a-112">Poznamenejte si okolnosti, za kterých došlo k chybě, a zavolejte služby Microsoft Product Support.</span><span class="sxs-lookup"><span data-stu-id="3d28a-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d28a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d28a-113">See also</span></span>

- [<span data-ttu-id="3d28a-114">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d28a-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="3d28a-115">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="3d28a-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="3d28a-116">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="3d28a-116">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
