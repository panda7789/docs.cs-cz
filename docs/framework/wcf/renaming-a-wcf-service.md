---
title: Přejmenování služby WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955139"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="4d1f5-102">Přejmenování služby WCF</span><span class="sxs-lookup"><span data-stu-id="4d1f5-102">Renaming a WCF Service</span></span>
<span data-ttu-id="4d1f5-103">Toto téma popisuje, jak můžete přejmenovat služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4d1f5-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="4d1f5-104">Přejmenování služby WCF</span><span class="sxs-lookup"><span data-stu-id="4d1f5-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="4d1f5-105">Proveďte následující kroky pro přejmenování služby v šabloně služby Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="4d1f5-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="4d1f5-106">Změňte název třídy, která implementuje služby.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="4d1f5-107">V konfiguračním souboru služby změňte název služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="4d1f5-108">Konfigurační soubor může být soubor app.config nebo web.config v závislosti na modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="4d1f5-109">Pokud je služba webhosted, používá soubor \*.svc.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="4d1f5-110">Otevřete soubor svc file a změnit název vaší služby, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="4d1f5-111">Tento krok není nezbytné pro aplikace v místním prostředí, protože není dostupný žádný soubor svc.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="4d1f5-112">Přejmenování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="4d1f5-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="4d1f5-113">Proveďte následující kroky pro přejmenování kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="4d1f5-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="4d1f5-114">Změňte název kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="4d1f5-115">V konfiguračním souboru služby změňte název kontraktu služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="4d1f5-116">Konfigurační soubor může být soubor app.config nebo web.config v závislosti na modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
