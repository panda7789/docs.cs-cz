---
title: "Nasazení služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75069b00fa07078ff0eb2d49e64f046d5415d154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-services"></a><span data-ttu-id="35b54-102">Nasazení služeb</span><span class="sxs-lookup"><span data-stu-id="35b54-102">Deploying Services</span></span>
<span data-ttu-id="35b54-103">Toto téma popisuje, jak můžete nasadit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace běhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="35b54-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="35b54-104">Výběr hostitelské prostředí pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="35b54-104">Choosing the Hosting Environment for Your Application</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="35b54-105">služby jsou určený ke spouštění v jakýkoli proces systému Windows, že podporuje spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="35b54-105"> services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="35b54-106">Stane aktivní, musí být hostované služby v rámci běhové prostředí, která ji vytvoří a určuje jeho kontextu a doba platnosti.</span><span class="sxs-lookup"><span data-stu-id="35b54-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="35b54-107">Hostování rozsah možnosti spuštění uvnitř nejjednodušší konzolové aplikace do prostředí serveru, jako je služba systému Windows, Internetové informační služby (IIS), nebo v rámci pracovní proces spravovat pomocí služby Aktivace systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="35b54-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="35b54-108">Chcete-li zkontrolovat různé možnosti hostování pro vaše [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, najdete v části [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="35b54-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b54-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="35b54-109">See Also</span></span>  
 [<span data-ttu-id="35b54-110">Hostování</span><span class="sxs-lookup"><span data-stu-id="35b54-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="35b54-111">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="35b54-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
