---
title: Nasazení rozhraní .NET Framework
description: Naučte se, jak nasadit rozhraní .NET pro vývojáře, kteří chtějí nainstalovat .NET s aplikacemi, a pro správce, kteří chtějí nasadit .NET přes síť.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
ms.openlocfilehash: 9e9fef2af56ca278b0e326c15546ca9f849a3253
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622767"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="b0d67-103">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b0d67-103">Deploying the .NET Framework</span></span>
<span data-ttu-id="b0d67-104">V této části dokumentace .NET Framework najdete informace pro vývojáře, kteří chtějí instalovat .NET Framework s aplikacemi a správci, kteří chtějí nasadit .NET Framework napříč sítí.</span><span class="sxs-lookup"><span data-stu-id="b0d67-104">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="b0d67-105">Popisuje také problémy s aktivací a restartováním související s nasazením a postup sledování průběhu instalace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0d67-105">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0d67-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b0d67-106">In This Section</span></span>  
 [<span data-ttu-id="b0d67-107">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b0d67-107">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)  
 <span data-ttu-id="b0d67-108">Vysvětluje, jak můžou vývojáři instalovat .NET Framework na počítačích uživatelů s jejich aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="b0d67-108">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="b0d67-109">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="b0d67-109">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)  
 <span data-ttu-id="b0d67-110">Vysvětluje, jak může správce systému nasadit .NET Framework a jeho systémové závislosti v síti pomocí služby Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="b0d67-110">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>  
  
 [<span data-ttu-id="b0d67-111">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b0d67-111">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)  
 <span data-ttu-id="b0d67-112">Popisuje správce restartování, který znemožňuje restartování, kdykoli je to možné, a vysvětluje, jak můžou aplikace, které instalují .NET Framework, využít.</span><span class="sxs-lookup"><span data-stu-id="b0d67-112">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="b0d67-113">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b0d67-113">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="b0d67-114">V této části najdete popis postupu při tichém spuštění a sledování procesu instalace .NET Framework při zobrazení vlastního zobrazení průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="b0d67-114">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="b0d67-115">.NET Framework – chyby inicializace: správa zkušeností uživatele</span><span class="sxs-lookup"><span data-stu-id="b0d67-115">.NET Framework Initialization Errors: Managing the User Experience</span></span>](initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="b0d67-116">Vysvětluje, co se stane, když aplikace .NET Framework vyžaduje verzi CLR, která je neplatná nebo není nainstalovaná v počítači uživatele, jak tyto chyby vyřešit a jak ovládat chybovou zprávu zobrazenou uživateli.</span><span class="sxs-lookup"><span data-stu-id="b0d67-116">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="b0d67-117">Postupy: Ladění problémů aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="b0d67-117">How to: Debug CLR Activation Issues</span></span>](how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="b0d67-118">Vysvětluje, jak můžete zobrazit a ladit protokoly aktivace CLR pro řešení problémů, ke kterým může dojít při nastavování aplikace pro spuštění se správnou verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b0d67-118">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d67-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0d67-119">See also</span></span>

- [<span data-ttu-id="b0d67-120">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="b0d67-120">Development Guide</span></span>](../development-guide.md)
