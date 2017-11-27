---
title: "Řešení potíží: Won aplikace služby & č. 39; t instalace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 82eb870761a7865385631cd9961ce99e0b0d3502
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="57902-102">Řešení potíží: Won aplikace služby & č. 39; t instalace</span><span class="sxs-lookup"><span data-stu-id="57902-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="57902-103">Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu znázorněné v instalačním programu pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="57902-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="57902-104">Hodnota musí být stejný v obou případech v pořadí pro vaši službu se správně nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="57902-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57902-105">Můžete také prohlédnout v protokolech instalace k získání zpětné vazby v procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="57902-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="57902-106">Také byste měli zkontrolovat zjistit, jestli máte jiné služby se stejným názvem již nainstalován.</span><span class="sxs-lookup"><span data-stu-id="57902-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="57902-107">Názvy služby musí být jedinečný pro instalace úspěšná.</span><span class="sxs-lookup"><span data-stu-id="57902-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57902-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="57902-108">See Also</span></span>  
 [<span data-ttu-id="57902-109">Úvod do aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="57902-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
