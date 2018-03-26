---
title: Přejmenování služby WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2ab3d780f85131fc7adf24c5f420bd5fe643d9e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="08674-102">Přejmenování služby WCF</span><span class="sxs-lookup"><span data-stu-id="08674-102">Renaming a WCF Service</span></span>
<span data-ttu-id="08674-103">Toto téma popisuje, jak můžete přejmenovat [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="08674-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="08674-104">Přejmenování služby WCF</span><span class="sxs-lookup"><span data-stu-id="08674-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="08674-105">Proveďte následující kroky pro přejmenování služby ve službě [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] šablony,</span><span class="sxs-lookup"><span data-stu-id="08674-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="08674-106">Změňte název třídy, který implementuje službu.</span><span class="sxs-lookup"><span data-stu-id="08674-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="08674-107">V konfiguračním souboru služby změňte název služby na nový název, který jste vybrali, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="08674-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="08674-108">Konfigurační soubor může být soubor app.config nebo web.config, v závislosti na hostování modelu.</span><span class="sxs-lookup"><span data-stu-id="08674-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="08674-109">Pokud je vaše služba webhosted, používá soubor \*.svc.</span><span class="sxs-lookup"><span data-stu-id="08674-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="08674-110">Otevřete soubor svc a změňte název vaší služby, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="08674-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="08674-111">Tento krok není nezbytné pro samoobslužné hostovaných aplikací, protože není dostupný žádný soubor svc.</span><span class="sxs-lookup"><span data-stu-id="08674-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="08674-112">Přejmenování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="08674-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="08674-113">Proveďte následující kroky pro přejmenování kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="08674-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="08674-114">Změňte název kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="08674-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="08674-115">V konfiguračním souboru služby změňte název kontraktu služby na nový název, který jste vybrali, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="08674-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="08674-116">Konfigurační soubor může být soubor app.config nebo web.config, v závislosti na hostování modelu.</span><span class="sxs-lookup"><span data-stu-id="08674-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
