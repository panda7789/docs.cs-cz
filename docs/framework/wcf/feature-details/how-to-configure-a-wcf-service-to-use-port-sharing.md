---
title: 'Postupy: Konfigurace používání sdílení portů ve službě WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: d66da04715f96dd37b8f36599d81924ec2f8d5cc
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778689"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="3ffed-102">Postupy: Konfigurace používání sdílení portů ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="3ffed-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="3ffed-103">Nejjednodušší způsob, jak používat sdílení v aplikaci Windows Communication Foundation (WCF) portu net.tcp:// je zveřejnit službu pomocí <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="3ffed-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="3ffed-104">Poskytuje tuto vazbu <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost, která určuje, zda je povoleno sdílení portu net.tcp:// služby konfigurován s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="3ffed-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="3ffed-105">Následující postup ukazuje, jak používat <xref:System.ServiceModel.NetTcpBinding> třídy v kódu a pak pomocí konfigurační prvky nejprve otevřete koncový bod na net.tcp://localhost/MyService identifikátor URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="3ffed-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="3ffed-106">Chcete povolit port net.tcp:// sdílení NetTcpBinding v kódu</span><span class="sxs-lookup"><span data-stu-id="3ffed-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1.  <span data-ttu-id="3ffed-107">Vytvoření služby k implementaci kontraktu volá `IMyService` a volejte jej `MyService`,.</span><span class="sxs-lookup"><span data-stu-id="3ffed-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <span data-ttu-id="3ffed-108">Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> třídy a nastavit <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="3ffed-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <span data-ttu-id="3ffed-109">Vytvoření <xref:System.ServiceModel.ServiceHost> a přidejte do ní pro koncový bod služby `MyService` , který používá port povoleno sdílení <xref:System.ServiceModel.NetTcpBinding> a že naslouchá na koncovém bodu řešit URI "net.tcp://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="3ffed-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="3ffed-110">Tento příklad používá výchozí port TCP 808, protože adresa koncového bodu identifikátor URI neurčuje jiné číslo portu.</span><span class="sxs-lookup"><span data-stu-id="3ffed-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="3ffed-111">Vzhledem k tomu, že port je explicitně povoleno sdílení u vazby přenosu, tato služba může sdílet port 808 s dalšími službami v jiných procesech.</span><span class="sxs-lookup"><span data-stu-id="3ffed-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="3ffed-112">Pokud nebyly povoleno sdílení portu a portu 808 se již používá jiná aplikace, tato služba vede <xref:System.ServiceModel.AddressAlreadyInUseException> kdy byl otevřen.</span><span class="sxs-lookup"><span data-stu-id="3ffed-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="3ffed-113">Chcete povolit port net.tcp:// sdílení NetTcpBinding v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="3ffed-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1.  <span data-ttu-id="3ffed-114">Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby pomocí konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="3ffed-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ffed-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ffed-115">See Also</span></span>  
 [<span data-ttu-id="3ffed-116">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="3ffed-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="3ffed-117">Postupy: Povolení služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="3ffed-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
