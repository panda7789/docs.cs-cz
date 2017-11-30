---
title: "Postupy: Konfigurace klienta základní Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: "47"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1f4d6b5386e82a2052182ba3f4a929de13b27c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="f0f4f-102">Postupy: Konfigurace klienta základní Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f0f4f-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="f0f4f-103">Toto je pátý šesti úkoly vyžadované pro vytvoření základní [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-103">This is the fifth of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="f0f4f-104">Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="f0f4f-105">Toto téma disuccess konfiguračního souboru klienta, který byl vytvořen pomocí funkce Přidat odkaz na službu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4f-105">This topic disuccess the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="f0f4f-106">Konfigurace klienta se skládá z určení koncového bodu, který klient používá k přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="f0f4f-107">Koncový bod má adresy, vazby a kontraktu a každý z nich musí být zadán právě konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="f0f4f-108">Abyste mohli nakonfigurovat klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f0f4f-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="f0f4f-109">Otevřete generovaný konfigurační soubor (App.config) z GettingStartedClient projektu.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="f0f4f-110">V následujícím příkladu je zobrazení generovaného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="f0f4f-111">V části [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) část, vyhledejte [ \<endpoint >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     <span data-ttu-id="f0f4f-112">Tento příklad konfiguruje koncového bodu, který klient používá k přístupu ke službě, který se nachází na následující adrese: http://localhost: 8000/ServiceModelSamples/Service/CalculatorService</span><span class="sxs-lookup"><span data-stu-id="f0f4f-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="f0f4f-113">Element koncového bodu určuje, že `ServiceReference1.ICalculator` kontrakt služby se používá ke komunikaci mezi klienta WCF a službou.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="f0f4f-114">Kanál WCF je nakonfigurován s poskytované systémem <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-114">The WCF channel is configured with the system-provided <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span></span> <span data-ttu-id="f0f4f-115">Tento kontrakt byl vytvořen pomocí přidat odkaz na službu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="f0f4f-116">Je v podstatě kopií kontrakt, který byl definován v GettingStartedLib projektu.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="f0f4f-117"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> Vazba určuje HTTP jako přenos, umožňuje vzájemnou spolupráci zabezpečení a další podrobnosti o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f0f4f-117">The <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f0f4f-118">Pomocí této konfigurace pomocí generovaného klienta najdete v tématu [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4f-118"> how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f4f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0f4f-119">See Also</span></span>  
 [<span data-ttu-id="f0f4f-120">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f0f4f-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="f0f4f-121">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f0f4f-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="f0f4f-122">Postupy: vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="f0f4f-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="f0f4f-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f0f4f-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="f0f4f-124">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="f0f4f-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
