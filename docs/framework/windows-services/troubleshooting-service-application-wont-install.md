---
title: 'Řešení potíží: Aplikace služby se nenainstaluje'
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
ms.openlocfilehash: f75a2f33ecde408d2d8e2f2343197ba56c4b8c21
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143816"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="a6a41-102">Řešení potíží: Aplikace služby se nenainstaluje</span><span class="sxs-lookup"><span data-stu-id="a6a41-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="a6a41-103">Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu uvedené v instalačním programu pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="a6a41-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="a6a41-104">Hodnota musí být stejné v obou případech v pořadí pro vaši službu nenainstaluje správně.</span><span class="sxs-lookup"><span data-stu-id="a6a41-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6a41-105">Můžete se také podívat na protokoly instalace získat zpětnou vazbu týkající se procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="a6a41-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="a6a41-106">Měli byste zkontrolovat také k určení, jestli máte jiné služby se stejným názvem už nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="a6a41-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="a6a41-107">Názvy služeb musí být jedinečný pro aby byla instalace úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a6a41-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a41-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6a41-108">See also</span></span>

- [<span data-ttu-id="a6a41-109">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="a6a41-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
