---
title: 'Řešení potíží: Aplikace služby se nenainstaluje'
description: Řešení potíží, pokud se aplikace služby nenainstaluje Přesvědčte se, zda je správně nastavena vlastnost ServiceName pro třídu služby.
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
ms.openlocfilehash: 4a57fb6975a6ded48abf7c8fd7eacec16e4f94d8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925524"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="e1aae-104">Řešení potíží: Aplikace služby se nenainstaluje</span><span class="sxs-lookup"><span data-stu-id="e1aae-104">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="e1aae-105">Pokud nebude aplikace služby správně nainstalována, zkontrolujte, zda je <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro třídu služby nastavena na stejnou hodnotu, jako je uvedena v instalačním programu této služby.</span><span class="sxs-lookup"><span data-stu-id="e1aae-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="e1aae-106">Aby se služba správně nainstalovala, musí být tato hodnota v obou instancích stejná.</span><span class="sxs-lookup"><span data-stu-id="e1aae-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1aae-107">Můžete se také podívat na protokoly instalace a získat zpětnou vazbu k procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="e1aae-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="e1aae-108">Měli byste také ověřit, jestli už máte nainstalovanou jinou službu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="e1aae-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="e1aae-109">Aby instalace proběhla úspěšně, musí být názvy služby jedinečné.</span><span class="sxs-lookup"><span data-stu-id="e1aae-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1aae-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1aae-110">See also</span></span>

- [<span data-ttu-id="e1aae-111">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="e1aae-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
