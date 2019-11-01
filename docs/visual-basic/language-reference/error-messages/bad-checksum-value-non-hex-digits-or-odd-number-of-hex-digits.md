---
title: Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 1ae4113505ca63df9b20e6e71aa0b418da4ef924
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197345"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="d63d8-102">Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.</span><span class="sxs-lookup"><span data-stu-id="d63d8-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="d63d8-103">Hodnota kontrolního součtu obsahuje neplatné hexadecimální číslice nebo má lichý počet číslic.</span><span class="sxs-lookup"><span data-stu-id="d63d8-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="d63d8-104">Když ASP.NET vygeneruje zdrojový soubor Visual Basic (přípona. vb), vypočítá kontrolní součet a umístí ho do skrytého zdrojového souboru identifikovaného `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="d63d8-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="d63d8-105">Je možné, že uživatel vygeneruje soubor. vb k tomu, ale tento postup je nejvhodnější pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="d63d8-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="d63d8-106">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="d63d8-106">By default, this message is a warning.</span></span> <span data-ttu-id="d63d8-107">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d63d8-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d63d8-108">**ID chyby:** BC42033</span><span class="sxs-lookup"><span data-stu-id="d63d8-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d63d8-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d63d8-109">To correct this error</span></span>  
  
1. <span data-ttu-id="d63d8-110">Pokud ASP.NET generuje zdrojový soubor Visual Basic, restartujte sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="d63d8-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2. <span data-ttu-id="d63d8-111">Pokud toto upozornění přetrvává po restartování, přeinstalujte ASP.NET a zkuste sestavení znovu.</span><span class="sxs-lookup"><span data-stu-id="d63d8-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3. <span data-ttu-id="d63d8-112">Pokud upozornění stále přetrvává nebo pokud nepoužíváte ASP.NET, shromážděte informace o okolnostech a upozorněte služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="d63d8-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d63d8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d63d8-113">See also</span></span>

- [<span data-ttu-id="d63d8-114">ASP.NET – přehled</span><span class="sxs-lookup"><span data-stu-id="d63d8-114">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="d63d8-115">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="d63d8-115">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
