---
title: 'Řešení potíží: Aplikace služby se nenainstaluje.'
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
ms.openlocfilehash: c45ab03ec4577d88953b0e43531082a46c29e8fd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053537"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="ba265-102">Řešení potíží: Aplikace služby se nenainstaluje.</span><span class="sxs-lookup"><span data-stu-id="ba265-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="ba265-103">Pokud nebude aplikace služby správně nainstalována, zkontrolujte, zda je <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro třídu služby nastavena na stejnou hodnotu, jako je uvedena v instalačním programu této služby.</span><span class="sxs-lookup"><span data-stu-id="ba265-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="ba265-104">Aby se služba správně nainstalovala, musí být tato hodnota v obou instancích stejná.</span><span class="sxs-lookup"><span data-stu-id="ba265-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba265-105">Můžete se také podívat na protokoly instalace a získat zpětnou vazbu k procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="ba265-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="ba265-106">Měli byste také ověřit, jestli už máte nainstalovanou jinou službu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="ba265-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="ba265-107">Aby instalace proběhla úspěšně, musí být názvy služby jedinečné.</span><span class="sxs-lookup"><span data-stu-id="ba265-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba265-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba265-108">See also</span></span>

- [<span data-ttu-id="ba265-109">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="ba265-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
