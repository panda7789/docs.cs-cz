---
title: "Postupy: Konfigurace používání sdílení portů ve službě WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db9242d76c34be2968d713e4c0380db99d19f1bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="d6489-102">Postupy: Konfigurace používání sdílení portů ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="d6489-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="d6489-103">Nejjednodušší způsob, jak používat sdílení v portu net.tcp:// vaše [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace je vystavit služby pomocí <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d6489-103">The easiest way to use net.tcp:// port sharing in your [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="d6489-104">Poskytuje tuto vazbu <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost, která určuje, zda je povoleno sdílení portů net.tcp:// pro službu konfigurován s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="d6489-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="d6489-105">Následující postup ukazuje, jak používat <xref:System.ServiceModel.NetTcpBinding> třída otevřete koncový bod v identifikátoru URI (Uniform Resource) net.tcp://localhost/MyService, nejprve v kódu a pak pomocí konfigurace – elementy.</span><span class="sxs-lookup"><span data-stu-id="d6489-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="d6489-106">Chcete-li povolit portu net.tcp:// sdílení na NetTcpBinding v kódu</span><span class="sxs-lookup"><span data-stu-id="d6489-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1.  <span data-ttu-id="d6489-107">Vytvoření služby implementace kontraktu názvem `IMyService` a pojmenujte ji `MyService`,.</span><span class="sxs-lookup"><span data-stu-id="d6489-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <span data-ttu-id="d6489-108">Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> a nastavit <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="d6489-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <span data-ttu-id="d6489-109">Vytvoření <xref:System.ServiceModel.ServiceHost> a přidejte do ní pro koncový bod služby `MyService` používající port povoleno sdílení <xref:System.ServiceModel.NetTcpBinding> a že sleduje na koncový bod adresy URI "net.tcp://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="d6489-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="d6489-110">Tento příklad používá výchozí port TCP 808, protože adresa koncového bodu URI neurčuje jiné číslo portu.</span><span class="sxs-lookup"><span data-stu-id="d6489-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="d6489-111">Protože sdílení portů je explicitně na přenos vazba povolena, tato služba může sdílet port 808 s jinými službami v jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="d6489-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="d6489-112">Pokud nebyly povoleno sdílení portů a port 808 se již používá jiná aplikace, tato služba by throw <xref:System.ServiceModel.AddressAlreadyInUseException> kdy byl otevřen.</span><span class="sxs-lookup"><span data-stu-id="d6489-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="d6489-113">Chcete-li povolit sdílení na NetTcpBinding v konfiguraci portu net.tcp://</span><span class="sxs-lookup"><span data-stu-id="d6489-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1.  <span data-ttu-id="d6489-114">Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby, pomocí konfigurace – elementy.</span><span class="sxs-lookup"><span data-stu-id="d6489-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6489-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6489-115">See Also</span></span>  
 [<span data-ttu-id="d6489-116">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d6489-116">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="d6489-117">Postupy: povolení služby Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d6489-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
