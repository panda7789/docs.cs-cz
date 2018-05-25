---
title: 'Řešení potíží: Služby aplikace Won&#39;t instalace'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
manager: douge
ms.openlocfilehash: 1f3e5674f9a52627efdc24d6c70c0ab16dcdbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="34da8-102">Řešení potíží: Služby aplikace Won&#39;t instalace</span><span class="sxs-lookup"><span data-stu-id="34da8-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="34da8-103">Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu znázorněné v instalačním programu pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="34da8-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="34da8-104">Hodnota musí být stejný v obou případech v pořadí pro vaši službu se správně nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="34da8-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34da8-105">Můžete také prohlédnout v protokolech instalace k získání zpětné vazby v procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="34da8-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="34da8-106">Také byste měli zkontrolovat zjistit, jestli máte jiné služby se stejným názvem již nainstalován.</span><span class="sxs-lookup"><span data-stu-id="34da8-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="34da8-107">Názvy služby musí být jedinečný pro instalace úspěšná.</span><span class="sxs-lookup"><span data-stu-id="34da8-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34da8-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="34da8-108">See Also</span></span>  
 [<span data-ttu-id="34da8-109">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="34da8-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
