---
title: 'Postupy: vytvoření služby WCF, který komunikuje přes objekty WebSockets'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: 197db0b81565b93c753ad3ecfb716e4d07ea1d0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493774"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="ca641-102">Postupy: vytvoření služby WCF, který komunikuje přes objekty WebSockets</span><span class="sxs-lookup"><span data-stu-id="ca641-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="ca641-103">Služby WCF a klienti mohou používat <xref:System.ServiceModel.NetHttpBinding> vazby pro komunikaci pomocí objekty WebSockets.</span><span class="sxs-lookup"><span data-stu-id="ca641-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="ca641-104">Technologie WebSockets bude použít, když <xref:System.ServiceModel.NetHttpBinding> určuje kontrakt služby definuje kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ca641-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="ca641-105">Toto téma popisuje, jak implementovat klienta, který používá a služby WCF <xref:System.ServiceModel.NetHttpBinding> komunikovat přes objekty WebSockets.</span><span class="sxs-lookup"><span data-stu-id="ca641-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="ca641-106">Zadejte službu</span><span class="sxs-lookup"><span data-stu-id="ca641-106">Define the Service</span></span>  
  
1.  <span data-ttu-id="ca641-107">Definování kontraktu zpětného volání</span><span class="sxs-lookup"><span data-stu-id="ca641-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="ca641-108">Tato smlouva se provádí klientská aplikace lze umožnit službě odesílat zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="ca641-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2.  <span data-ttu-id="ca641-109">Definování kontraktu služby a zadejte `IStockQuoteCallback` rozhraní jako kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ca641-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3.  <span data-ttu-id="ca641-110">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="ca641-110">Implement the service contract.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="ca641-111">Operace služby `StartSendingQuotes` je implementovaný jako asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="ca641-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="ca641-112">Nemůžeme načíst pomocí kanálu zpětného volání `OperationContext` a pokud je otevřít kanál, provedeme asynchronní volání na zpětné volání kanálu.</span><span class="sxs-lookup"><span data-stu-id="ca641-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4.  <span data-ttu-id="ca641-113">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="ca641-113">Configure the service</span></span>  
  
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
  
     <span data-ttu-id="ca641-114">Konfigurační soubor služby spoléhá na koncových bodů WCF na výchozí.</span><span class="sxs-lookup"><span data-stu-id="ca641-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="ca641-115">`<protocolMapping>` Části slouží k určení, který `NetHttpBinding` má být použit pro výchozí koncové body vytvořili.</span><span class="sxs-lookup"><span data-stu-id="ca641-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="ca641-116">Definování klienta</span><span class="sxs-lookup"><span data-stu-id="ca641-116">Define the Client</span></span>  
  
1.  <span data-ttu-id="ca641-117">Implementujte kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ca641-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="ca641-118">Operace zpětného kontrakt je implementovaný jako asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="ca641-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1.  <span data-ttu-id="ca641-119">Implementaci kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="ca641-119">Implement the client code.</span></span>  
  
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
  
         <span data-ttu-id="ca641-120">Hodnota CallbackHandler se zde opakuje pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="ca641-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="ca641-121">Klientská aplikace vytvoří nový objekt InstanceContext a určuje implementace rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ca641-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="ca641-122">Potom vytvoří instanci třídy proxy odesílání odkaz na nově vytvořený objekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="ca641-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="ca641-123">Když klient zavolá službu, službu bude volat klienta pomocí zadané kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ca641-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2.  <span data-ttu-id="ca641-124">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="ca641-124">Configure the client</span></span>  
  
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
  
         <span data-ttu-id="ca641-125">Není co speciální, je nutné provést v konfiguraci klienta, zadat pouze na klientské straně koncový bod pomocí `NetHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="ca641-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca641-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca641-126">Example</span></span>  
 <span data-ttu-id="ca641-127">Následuje kód dokončení použít v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ca641-127">The following is the complete code used in this topic.</span></span>  
  
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
  
```  
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
  http://go.microsoft.com/fwlink/?LinkId=169433  
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
<!—App.config -->  
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
  
## <a name="see-also"></a><span data-ttu-id="ca641-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca641-128">See Also</span></span>  
 [<span data-ttu-id="ca641-129">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="ca641-129">Synchronous and Asynchronous Operations</span></span>](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [<span data-ttu-id="ca641-130">Používání NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ca641-130">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)
