---
title: 'Postupy: Konfigurace používání sdílení portů ve službě WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 28f2858d68de99839d7fec66b0fe4528d7e42325
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579524"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="18ff8-102">Postupy: Konfigurace používání sdílení portů ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="18ff8-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="18ff8-103">Nejjednodušší způsob, jak použít sdílení NET. TCP://port v aplikaci Windows Communication Foundation (WCF), je vystavit službu pomocí <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="18ff8-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="18ff8-104">Tato vazba poskytuje <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost, která určuje, zda je povoleno sdílení NET. TCP://port pro službu konfigurovanou s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="18ff8-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="18ff8-105">Následující postup ukazuje, jak použít <xref:System.ServiceModel.NetTcpBinding> třídu k otevření koncového bodu v identifikátoru URI (Uniform Resource Identifier) NET. TCP://localhost/MyService, nejprve v kódu a poté pomocí konfiguračních elementů.</span><span class="sxs-lookup"><span data-stu-id="18ff8-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="18ff8-106">Povolení sdílení NET. TCP://port na NetTcpBinding v kódu</span><span class="sxs-lookup"><span data-stu-id="18ff8-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="18ff8-107">Vytvořte službu pro implementaci kontraktu s názvem `IMyService` a zavolejte na něj `MyService` .</span><span class="sxs-lookup"><span data-stu-id="18ff8-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="18ff8-108">Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy a nastavte <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost na `true` .</span><span class="sxs-lookup"><span data-stu-id="18ff8-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="18ff8-109">Vytvořte <xref:System.ServiceModel.ServiceHost> a přidejte do něj koncový bod služby `MyService` , který používá sdílení portů <xref:System.ServiceModel.NetTcpBinding> a který naslouchá na identifikátoru URI adresy koncového bodu NET. TCP://localhost/MyService.</span><span class="sxs-lookup"><span data-stu-id="18ff8-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="18ff8-110">V tomto příkladu se používá výchozí port TCP 808, protože identifikátor URI adresy koncového bodu neurčuje jiné číslo portu.</span><span class="sxs-lookup"><span data-stu-id="18ff8-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="18ff8-111">Vzhledem k tomu, že sdílení portů je explicitně povoleno u přenosové vazby, může tato služba sdílet port 808 s dalšími službami v jiných procesech.</span><span class="sxs-lookup"><span data-stu-id="18ff8-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="18ff8-112">Pokud sdílení portů nebylo povoleno a jiná aplikace již používala port 808, tato služba vyvolá <xref:System.ServiceModel.AddressAlreadyInUseException> při otevření.</span><span class="sxs-lookup"><span data-stu-id="18ff8-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="18ff8-113">Povolení sdílení NET. TCP://port v NetTcpBinding v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="18ff8-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="18ff8-114">Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby pomocí elementů konfigurace.</span><span class="sxs-lookup"><span data-stu-id="18ff8-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18ff8-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="18ff8-115">See also</span></span>

- [<span data-ttu-id="18ff8-116">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="18ff8-116">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="18ff8-117">Postupy: Povolení služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="18ff8-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](how-to-enable-the-net-tcp-port-sharing-service.md)
