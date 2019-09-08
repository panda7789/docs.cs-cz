---
title: Nasazení služeb
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 684b781c568518cfb321d8021e4f7062e855e6aa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798139"
---
# <a name="deploying-services"></a><span data-ttu-id="367b8-102">Nasazení služeb</span><span class="sxs-lookup"><span data-stu-id="367b8-102">Deploying Services</span></span>
<span data-ttu-id="367b8-103">Toto téma popisuje, jak lze nasadit aplikaci Windows Communication Foundation (WCF) do prostředí Runtime.</span><span class="sxs-lookup"><span data-stu-id="367b8-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="367b8-104">Výběr hostitelského prostředí pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="367b8-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="367b8-105">Služby WCF jsou navržené tak, aby běžely v jakémkoli procesu Windows, který podporuje spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="367b8-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="367b8-106">Aby bylo možné stát aktivní, musí být služba hostována v prostředí runtime, které je vytvoří a řídí její kontext a dobu života.</span><span class="sxs-lookup"><span data-stu-id="367b8-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="367b8-107">Hostování možností v rámci nejjednodušších konzolových aplikací na serverová prostředí, jako je například služba systému Windows, Internetová informační služba (IIS) nebo v rámci pracovního procesu spravovaného aktivační službou systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="367b8-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="367b8-108">Chcete-li si projít různé možnosti hostování vaší aplikace WCF, přečtěte si informace o [hostitelských službách](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="367b8-108">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367b8-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="367b8-109">See also</span></span>

- [<span data-ttu-id="367b8-110">Hostování</span><span class="sxs-lookup"><span data-stu-id="367b8-110">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="367b8-111">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="367b8-111">Hosting Services</span></span>](../hosting-services.md)
