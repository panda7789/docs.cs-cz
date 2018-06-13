---
title: Nasazení služeb
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 4d9efcb4da064021d93345285982c0cbd29dde2e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803579"
---
# <a name="deploying-services"></a><span data-ttu-id="15173-102">Nasazení služeb</span><span class="sxs-lookup"><span data-stu-id="15173-102">Deploying Services</span></span>
<span data-ttu-id="15173-103">Toto téma popisuje, jak můžete nasadit aplikace systému Windows Communication Foundation (WCF) do běhu prostředí.</span><span class="sxs-lookup"><span data-stu-id="15173-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="15173-104">Výběr hostitelské prostředí pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="15173-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="15173-105">Služby WCF jsou určený ke spouštění v jakýkoli proces systému Windows, že podporuje spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="15173-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="15173-106">Stane aktivní, musí být hostované služby v rámci běhové prostředí, která ji vytvoří a určuje jeho kontextu a doba platnosti.</span><span class="sxs-lookup"><span data-stu-id="15173-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="15173-107">Hostování rozsah možnosti spuštění uvnitř nejjednodušší konzolové aplikace do prostředí serveru, jako je služba systému Windows, Internetové informační služby (IIS), nebo v rámci pracovní proces spravovat pomocí služby Aktivace systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="15173-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="15173-108">Různé možnosti hostování vaší aplikace WCF najdete v tématu [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="15173-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15173-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="15173-109">See Also</span></span>  
 [<span data-ttu-id="15173-110">Hostování</span><span class="sxs-lookup"><span data-stu-id="15173-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="15173-111">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="15173-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
