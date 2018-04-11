---
title: Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1158742c8eaa51bcbb5607795f16ae6c2b570db4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="0e801-102">Nesprávná hodnota kontrolního součtu. Číslice nejsou v šestnáctkové soustavě nebo je zadán lichý počet číslic v šestnáctkové soustavě.</span><span class="sxs-lookup"><span data-stu-id="0e801-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="0e801-103">Hodnota kontrolního součtu obsahuje neplatný šestnáctkové číslice nebo má lichý počet číslic.</span><span class="sxs-lookup"><span data-stu-id="0e801-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="0e801-104">Když ASP.NET generuje zdrojového souboru jazyka Visual Basic (VB rozšíření), vypočítá kontrolní součet a umístí jej do skryté zdrojového souboru identifikovaný `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="0e801-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="0e801-105">Je možné pro uživatele generování souboru VB k tomu taky, ale tento proces je nejlepší vlevo na interní použití.</span><span class="sxs-lookup"><span data-stu-id="0e801-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="0e801-106">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="0e801-106">By default, this message is a warning.</span></span> <span data-ttu-id="0e801-107">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0e801-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0e801-108">**ID chyby:** BC42033</span><span class="sxs-lookup"><span data-stu-id="0e801-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e801-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0e801-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="0e801-110">Vytváří-li ASP.NET zdrojový soubor jazyka Visual Basic, restartujte sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="0e801-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2.  <span data-ttu-id="0e801-111">Pokud toto upozornění přetrvává po restartování, přeinstalujte ASP.NET a opakujte sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e801-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3.  <span data-ttu-id="0e801-112">Pokud toto upozornění dál, nebo pokud nepoužíváte technologii ASP.NET, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="0e801-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e801-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e801-113">See Also</span></span>  
 [<span data-ttu-id="0e801-114">Přehled technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0e801-114">ASP.NET Overview</span></span>](https://msdn.microsoft.com/library/4w3ex9c2.aspx)  
 [<span data-ttu-id="0e801-115">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="0e801-115">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
