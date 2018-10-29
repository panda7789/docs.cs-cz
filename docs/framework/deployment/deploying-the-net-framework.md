---
title: Nasazení rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac17993a4980e96cbd05fc2523567138e7b56262
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196438"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="bea8f-102">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bea8f-102">Deploying the .NET Framework</span></span>
<span data-ttu-id="bea8f-103">Tato část dokumentace k rozhraní .NET Framework obsahuje informace pro vývojáře, kteří chtějí nainstalovat rozhraní .NET Framework pomocí svých aplikací a správce, kteří chtějí nasadit rozhraní .NET Framework přes síť.</span><span class="sxs-lookup"><span data-stu-id="bea8f-103">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="bea8f-104">Také popisuje aktivace a restartujte problémy spojené s nasazením a jak monitorovat průběh instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bea8f-104">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bea8f-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bea8f-105">In This Section</span></span>  
 [<span data-ttu-id="bea8f-106">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="bea8f-106">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 <span data-ttu-id="bea8f-107">Vysvětluje, jak vývojáři můžete nainstalovat rozhraní .NET Framework na jejich uživatele, počítače s jejich aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="bea8f-107">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="bea8f-108">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="bea8f-108">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
 <span data-ttu-id="bea8f-109">Vysvětluje, jak může správce systému můžete nasadit rozhraní .NET Framework a jeho systémové závislosti napříč sítí pomocí System Center Configuration Manageru (SCCM).</span><span class="sxs-lookup"><span data-stu-id="bea8f-109">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>  
  
 [<span data-ttu-id="bea8f-110">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="bea8f-110">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
 <span data-ttu-id="bea8f-111">Popisuje správce restartování se zabránilo restartuje kdykoli je to možné a vysvětluje, jak aplikace, které instalace rozhraní .NET Framework můžete využívat jejich výhod.</span><span class="sxs-lookup"><span data-stu-id="bea8f-111">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="bea8f-112">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="bea8f-112">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="bea8f-113">Popisuje, jak spustit bez upozornění a sledovat proces instalace rozhraní .NET Framework při vlastním zobrazením průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="bea8f-113">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="bea8f-114">.NET Framework – chyby inicializace: správa zkušeností uživatele</span><span class="sxs-lookup"><span data-stu-id="bea8f-114">.NET Framework Initialization Errors: Managing the User Experience</span></span>](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="bea8f-115">Vysvětluje, co se stane, když aplikace rozhraní .NET Framework požaduje verzi CLR, která je neplatná nebo není nainstalovaná na počítači uživatele, jak tyto chyby vyřešit a jak řídit zobrazí uživateli chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="bea8f-115">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="bea8f-116">Postupy: Ladění problémů aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="bea8f-116">How to: Debug CLR Activation Issues</span></span>](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="bea8f-117">Vysvětluje, jak lze zobrazit a ladění CLR aktivace protokoly k řešení potíží, které můžete narazit při získávání aplikace na spouštění se správnou verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="bea8f-117">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea8f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="bea8f-118">See Also</span></span>  
- [<span data-ttu-id="bea8f-119">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="bea8f-119">Development Guide</span></span>](../../../docs/framework/development-guide.md)
