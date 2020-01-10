---
title: Nasazení rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
ms.openlocfilehash: cc4f9c38138a37b6068d33ffa4229a955db08c07
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716550"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="8cb66-102">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8cb66-102">Deploying the .NET Framework</span></span>
<span data-ttu-id="8cb66-103">V této části dokumentace .NET Framework najdete informace pro vývojáře, kteří chtějí instalovat .NET Framework s aplikacemi a správci, kteří chtějí nasadit .NET Framework napříč sítí.</span><span class="sxs-lookup"><span data-stu-id="8cb66-103">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="8cb66-104">Popisuje také problémy s aktivací a restartováním související s nasazením a postup sledování průběhu instalace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8cb66-104">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8cb66-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8cb66-105">In This Section</span></span>  
 [<span data-ttu-id="8cb66-106">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8cb66-106">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)  
 <span data-ttu-id="8cb66-107">Vysvětluje, jak můžou vývojáři instalovat .NET Framework na počítačích uživatelů s jejich aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="8cb66-107">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="8cb66-108">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="8cb66-108">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)  
 <span data-ttu-id="8cb66-109">Vysvětluje, jak může správce systému nasadit .NET Framework a jeho systémové závislosti v síti pomocí služby Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="8cb66-109">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>  
  
 [<span data-ttu-id="8cb66-110">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8cb66-110">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)  
 <span data-ttu-id="8cb66-111">Popisuje správce restartování, který znemožňuje restartování, kdykoli je to možné, a vysvětluje, jak můžou aplikace, které instalují .NET Framework, využít.</span><span class="sxs-lookup"><span data-stu-id="8cb66-111">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="8cb66-112">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8cb66-112">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="8cb66-113">V této části najdete popis postupu při tichém spuštění a sledování procesu instalace .NET Framework při zobrazení vlastního zobrazení průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="8cb66-113">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="8cb66-114">.NET Framework – chyby inicializace: správa zkušeností uživatele</span><span class="sxs-lookup"><span data-stu-id="8cb66-114">.NET Framework Initialization Errors: Managing the User Experience</span></span>](initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="8cb66-115">Vysvětluje, co se stane, když aplikace .NET Framework vyžaduje verzi CLR, která je neplatná nebo není nainstalovaná v počítači uživatele, jak tyto chyby vyřešit a jak ovládat chybovou zprávu zobrazenou uživateli.</span><span class="sxs-lookup"><span data-stu-id="8cb66-115">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="8cb66-116">Postupy: Ladění problémů aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="8cb66-116">How to: Debug CLR Activation Issues</span></span>](how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="8cb66-117">Vysvětluje, jak můžete zobrazit a ladit protokoly aktivace CLR pro řešení problémů, ke kterým může dojít při nastavování aplikace pro spuštění se správnou verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8cb66-117">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb66-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cb66-118">See also</span></span>

- [<span data-ttu-id="8cb66-119">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="8cb66-119">Development Guide</span></span>](../development-guide.md)
