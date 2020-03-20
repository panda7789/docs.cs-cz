---
title: 'Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: d420ac8fcb98ddec195093be8ae25be37443da4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184980"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="7ecd7-102">Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets</span><span class="sxs-lookup"><span data-stu-id="7ecd7-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="7ecd7-103">WCF služby a <xref:System.ServiceModel.NetHttpBinding> klienti mohou použít vazbu ke komunikaci přes WebSockets.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="7ecd7-104">WebSockets bude použit, <xref:System.ServiceModel.NetHttpBinding> když určuje servisní smlouvy definuje smlouvu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="7ecd7-105">Toto téma popisuje, jak implementovat službu <xref:System.ServiceModel.NetHttpBinding> WCF a klienta, který používá ke komunikaci přes WebSockets.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="7ecd7-106">Definování služby</span><span class="sxs-lookup"><span data-stu-id="7ecd7-106">Define the Service</span></span>  
  
1. <span data-ttu-id="7ecd7-107">Definování smlouvy zpětného volání</span><span class="sxs-lookup"><span data-stu-id="7ecd7-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="7ecd7-108">Tato smlouva bude implementována klientskou aplikací, aby služba mohla odesílat zprávy zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2. <span data-ttu-id="7ecd7-109">Definujte servisní smlouvu `IStockQuoteCallback` a zadejte rozhraní jako kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3. <span data-ttu-id="7ecd7-110">Implementujte servisní smlouvu.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-110">Implement the service contract.</span></span>  
  
    ```csharp
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  

            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="7ecd7-111">Operace `StartSendingQuotes` služby je implementována jako asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="7ecd7-112">Načteme kanál zpětného `OperationContext` volání pomocí a pokud je kanál otevřený, provedeme asynchronní volání kanálu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4. <span data-ttu-id="7ecd7-113">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="7ecd7-113">Configure the service</span></span>  
  
    ```xml  
    <configuration>  
        <appSettings>  
          <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />
        </appSettings>  
        <system.web>  
          <compilation debug="true" targetFramework="4.5" />
        </system.web>  
        <system.serviceModel>  
            <protocolMapping>  
              <add scheme="http" binding="netHttpBinding"/>  
              <add scheme="https" binding="netHttpsBinding"/>  
            </protocolMapping>  
            <behaviors>  
                <serviceBehaviors>  
                    <behavior name="">  
                        <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                        <serviceDebug includeExceptionDetailInFaults="false" />  
                    </behavior>  
                </serviceBehaviors>  
            </behaviors>  
            <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
                multipleSiteBindingsEnabled="true" />  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="7ecd7-114">Konfigurační soubor služby závisí na výchozíkoncové body WCF.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="7ecd7-115">Oddíl `<protocolMapping>` se používá k `NetHttpBinding` určení, že by měl být použit pro výchozí vytvořené koncové body.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="7ecd7-116">Definovat klienta</span><span class="sxs-lookup"><span data-stu-id="7ecd7-116">Define the Client</span></span>  
  
1. <span data-ttu-id="7ecd7-117">Implementujte kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="7ecd7-118">Operace smlouvy zpětného volání je implementována jako asynchronní metoda.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1. <span data-ttu-id="7ecd7-119">Implementujte kód klienta.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-119">Implement the client code.</span></span>  
  
        ```csharp  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                var context = new InstanceContext(new CallbackHandler());  
                var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
                client.StartSendingQuotes();
                Console.ReadLine();  
            }  
  
            private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
        }  
        ```  
  
         <span data-ttu-id="7ecd7-120">CallbackHandler se opakuje zde pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="7ecd7-121">Klientská aplikace vytvoří nový InstanceContext a určuje implementaci rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="7ecd7-122">Dále vytvoří instanci třídy proxy, která odesílá odkaz na nově vytvořený InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="7ecd7-123">Když klient volá službu, služba zavolá klientovi pomocí zadané smlouvy zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2. <span data-ttu-id="7ecd7-124">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="7ecd7-124">Configure the client</span></span>  
  
        ```xml  
        <?xml version="1.0" encoding="utf-8" ?>  
        <configuration>  
            <startup>
                <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
            </startup>  
            <system.serviceModel>  
                <bindings>  
                    <netHttpBinding>  
                        <binding name="NetHttpBinding_IStockQuoteService">  
                            <webSocketSettings transportUsage="Always" />  
                        </binding>  
                    </netHttpBinding>  
                </bindings>  
                <client>  
                    <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                        binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                        contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
                </client>  
            </system.serviceModel>  
        </configuration>  
        ```  
  
         <span data-ttu-id="7ecd7-125">Není nic zvláštního, co musíte udělat v konfiguraci klienta, `NetHttpBinding`stačí zadat koncový bod na straně klienta pomocí .</span><span class="sxs-lookup"><span data-stu-id="7ecd7-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ecd7-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ecd7-126">Example</span></span>  
 <span data-ttu-id="7ecd7-127">Následuje úplný kód použitý v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7ecd7-127">The following is the complete code used in this topic.</span></span>  
  
```csharp  
// IStockQuoteService.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
    public interface IStockQuoteService  
    {  
        [OperationContract(IsOneWay = true)]  
        Task StartSendingQuotes();  
    }  
  
    [ServiceContract]  
    public interface IStockQuoteCallback  
    {  
        [OperationContract(IsOneWay = true)]  
        Task SendQuote(string code, double value);  
    }  
}  
```  
  
```csharp
// StockQuoteService.svc.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  
  
            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
}  
```  
  
```xml  
<?xml version="1.0"?>  
  
<!--  
  For more information on how to configure your ASP.NET application, please visit  
  https://go.microsoft.com/fwlink/?LinkId=169433  
  -->  
  
<configuration>  
    <appSettings>  
      <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />
    </appSettings>  
    <system.web>  
      <compilation debug="true" targetFramework="4.5" />
    </system.web>  
    <system.serviceModel>  
        <protocolMapping>  
          <add scheme="http" binding="netHttpBinding"/>  
          <add scheme="https" binding="netHttpsBinding"/>  
        </protocolMapping>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="">  
                    <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                    <serviceDebug includeExceptionDetailInFaults="false" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
        <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
            multipleSiteBindingsEnabled="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
```
<!-- StockQuoteService.svc -->  
<%@ ServiceHost Language="C#" Debug="true" Service="Server.StockQuoteService" CodeBehind="StockQuoteService.svc.cs" %>  
```  
  
```csharp  
// Client.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            var context = new InstanceContext(new CallbackHandler());  
            var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
            client.StartSendingQuotes();
            Console.ReadLine();  
        }  
  
        private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
        {  
            public async Task SendQuoteAsync(string code, double value)  
            {  
                Console.WriteLine("{0}: {1:f2}", code, value);  
            }  
        }  
    }  
}  
```  
  
```xml  
<!--App.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
    </startup>  
    <system.serviceModel>  
        <bindings>  
            <netHttpBinding>  
                <binding name="NetHttpBinding_IStockQuoteService">  
                    <webSocketSettings transportUsage="Always" />  
                </binding>  
            </netHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ecd7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ecd7-128">See also</span></span>

- [<span data-ttu-id="7ecd7-129">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="7ecd7-129">Synchronous and Asynchronous Operations</span></span>](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="7ecd7-130">Používání vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7ecd7-130">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)
