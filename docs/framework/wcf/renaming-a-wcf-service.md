---
title: Přejmenování služby WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052049"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="2ca73-102">Přejmenování služby WCF</span><span class="sxs-lookup"><span data-stu-id="2ca73-102">Renaming a WCF Service</span></span>
<span data-ttu-id="2ca73-103">Toto téma popisuje, jak lze přejmenovat službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2ca73-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="2ca73-104">Přejmenování služby WCF</span><span class="sxs-lookup"><span data-stu-id="2ca73-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="2ca73-105">Provedením následujících kroků přejmenujete službu v šabloně Windows Communication Foundation (WCF),</span><span class="sxs-lookup"><span data-stu-id="2ca73-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="2ca73-106">Změňte název třídy, která implementuje službu.</span><span class="sxs-lookup"><span data-stu-id="2ca73-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="2ca73-107">V konfiguračním souboru služby změňte název služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2ca73-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="2ca73-108">Konfigurační soubor může být buď app.config, nebo web.config soubor v závislosti na modelu hostování.</span><span class="sxs-lookup"><span data-stu-id="2ca73-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="2ca73-109">Pokud je vaše služba hostitelem webhostovaná, používá soubor \* \* . svc\* .</span><span class="sxs-lookup"><span data-stu-id="2ca73-109">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="2ca73-110">Otevřete soubor svc a upravte název vaší služby, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2ca73-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="2ca73-111">Tento krok není nutný pro samoobslužné aplikace, protože není k dispozici žádný soubor svc.</span><span class="sxs-lookup"><span data-stu-id="2ca73-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="2ca73-112">Přejmenování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="2ca73-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="2ca73-113">Chcete-li přejmenovat kontrakt služby, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="2ca73-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="2ca73-114">Změňte název kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="2ca73-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="2ca73-115">V konfiguračním souboru služby změňte název kontraktu služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2ca73-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="2ca73-116">Konfigurační soubor může být buď app.config, nebo web.config soubor v závislosti na modelu hostování.</span><span class="sxs-lookup"><span data-stu-id="2ca73-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
