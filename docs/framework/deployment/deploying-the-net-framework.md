---
title: "Nasazení rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1320c0364b1fdc3a67d2ac99d0591f37044c36a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="9862d-102">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9862d-102">Deploying the .NET Framework</span></span>
<span data-ttu-id="9862d-103">V této části dokumentace rozhraní .NET Framework poskytuje informace pro vývojáře, kteří chtějí nainstalovat rozhraní .NET Framework s jejich aplikace a správci, kteří chtějí nasadit rozhraní .NET Framework v síti.</span><span class="sxs-lookup"><span data-stu-id="9862d-103">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="9862d-104">Také popisuje aktivace a restartujte problémů, souvisejících s nasazení, jak můžete sledovat průběh instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9862d-104">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9862d-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9862d-105">In This Section</span></span>  
 [<span data-ttu-id="9862d-106">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="9862d-106">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 <span data-ttu-id="9862d-107">Vysvětluje, jak vývojáři můžete nainstalovat rozhraní .NET Framework na své uživatele, počítače s aplikací.</span><span class="sxs-lookup"><span data-stu-id="9862d-107">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="9862d-108">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="9862d-108">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
 <span data-ttu-id="9862d-109">Vysvětluje, jak správce systému můžete nasadit rozhraní .NET Framework a jeho závislé součásti systému přes síť pomocí System Center Configuration Manager (SCCM).</span><span class="sxs-lookup"><span data-stu-id="9862d-109">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>  
  
 [<span data-ttu-id="9862d-110">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9862d-110">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
 <span data-ttu-id="9862d-111">Popisuje správce restartovat, aby se zabránilo restartuje, pokud je to možné a vysvětluje, jak aplikace, které instalaci rozhraní .NET Framework, můžete využít výhod ho.</span><span class="sxs-lookup"><span data-stu-id="9862d-111">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="9862d-112">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9862d-112">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="9862d-113">Popisuje, jak bezobslužná spustit a sledovat proces instalace rozhraní .NET Framework při zobrazování zobrazení průběh instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="9862d-113">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="9862d-114">.NET Framework – chyby inicializace: správa zkušeností uživatele</span><span class="sxs-lookup"><span data-stu-id="9862d-114">.NET Framework Initialization Errors: Managing the User Experience</span></span>](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="9862d-115">Vysvětluje, co se stane, když aplikace rozhraní .NET Framework požaduje verze CLR, který je neplatná nebo není nainstalována v počítači uživatele, jak vyřešit tyto chyby a jak ovládat chybová zpráva zobrazovat uživateli.</span><span class="sxs-lookup"><span data-stu-id="9862d-115">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="9862d-116">Postupy: Ladění problémů aktivace CLR</span><span class="sxs-lookup"><span data-stu-id="9862d-116">How to: Debug CLR Activation Issues</span></span>](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="9862d-117">Vysvětluje, jak můžete zobrazit a ladění protokoly aktivace CLR vyřešit problémy, ke kterým může dojít při získávání aplikace na spouštění s správná verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="9862d-117">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9862d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9862d-118">See Also</span></span>  
 [<span data-ttu-id="9862d-119">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="9862d-119">Development Guide</span></span>](../../../docs/framework/development-guide.md)
