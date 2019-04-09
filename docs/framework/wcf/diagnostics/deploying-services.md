---
title: Nasazení služeb
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 2c3cd17b597fafcd02b9155089bc583fafbc9dea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085751"
---
# <a name="deploying-services"></a><span data-ttu-id="602a9-102">Nasazení služeb</span><span class="sxs-lookup"><span data-stu-id="602a9-102">Deploying Services</span></span>
<span data-ttu-id="602a9-103">Toto téma popisuje, jak můžete nasadit aplikaci Windows Communication Foundation (WCF) na prostředí za běhu.</span><span class="sxs-lookup"><span data-stu-id="602a9-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="602a9-104">Výběr hostitelské prostředí pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="602a9-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="602a9-105">Služby WCF slouží ke spouštění v jakýkoli proces Windows, že podporuje spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="602a9-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="602a9-106">Přejít do aktivního stavu, musí být služba hostovaný v rámci prostředí za běhu, která ho vytvoří a řídí jeho kontextu a životnosti.</span><span class="sxs-lookup"><span data-stu-id="602a9-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="602a9-107">Hostování rozsah možnosti spuštění uvnitř nejjednodušší konzolovou aplikaci pro prostředí serveru jako služba Windows, Internetové informační služby (IIS), nebo v rámci pracovní proces spravované pomocí aktivace služby Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="602a9-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="602a9-108">Různé hostingové možnosti pro vaši aplikaci WCF najdete v tématu [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="602a9-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602a9-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="602a9-109">See also</span></span>

- [<span data-ttu-id="602a9-110">Hostování</span><span class="sxs-lookup"><span data-stu-id="602a9-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)
- [<span data-ttu-id="602a9-111">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="602a9-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
