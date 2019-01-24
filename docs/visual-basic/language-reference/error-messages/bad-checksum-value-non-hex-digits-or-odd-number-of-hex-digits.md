---
title: Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 211f07e7c9dbc7e0583272d46c493ad99628d283
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724106"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="2403e-102">Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.</span><span class="sxs-lookup"><span data-stu-id="2403e-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="2403e-103">Hodnota kontrolního součtu obsahuje neplatné hexadecimální číslice nebo má lichý počet číslic.</span><span class="sxs-lookup"><span data-stu-id="2403e-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="2403e-104">Když ASP.NET generuje zdrojový soubor jazyka Visual Basic (.vb rozšíření), vypočítá kontrolní součet a umístí jej do skryté zdrojový soubor identifikovaný `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="2403e-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="2403e-105">Je možné pro uživatele, generuje se soubor .vb k tomu taky, ale tento proces je nejlepší doleva na interní použití.</span><span class="sxs-lookup"><span data-stu-id="2403e-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="2403e-106">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="2403e-106">By default, this message is a warning.</span></span> <span data-ttu-id="2403e-107">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2403e-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2403e-108">**ID chyby:** BC42033</span><span class="sxs-lookup"><span data-stu-id="2403e-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2403e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2403e-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="2403e-110">Pokud technologie ASP.NET generuje zdrojový soubor jazyka Visual Basic, restartujte sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="2403e-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2.  <span data-ttu-id="2403e-111">Pokud toto upozornění zobrazuje i po restartování, přeinstalujte technologie ASP.NET a zkuste sestavení znovu.</span><span class="sxs-lookup"><span data-stu-id="2403e-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3.  <span data-ttu-id="2403e-112">Pokud se nepovede upozornění, nebo pokud nejsou pomocí technologie ASP.NET, shromážděte informace o okolnostech a upozorňovat Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="2403e-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2403e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2403e-113">See also</span></span>

- [<span data-ttu-id="2403e-114">ASP.NET: Přehled</span><span class="sxs-lookup"><span data-stu-id="2403e-114">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="2403e-115">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="2403e-115">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
