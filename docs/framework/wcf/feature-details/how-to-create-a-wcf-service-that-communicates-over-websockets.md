---
title: 'Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: 80c62ddc6630d26c6c178d1eeff8c6df05bf1d00
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051932"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="9abce-102">Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets</span><span class="sxs-lookup"><span data-stu-id="9abce-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="9abce-103">Služby a Klienti WCF mohou pomocí <xref:System.ServiceModel.NetHttpBinding> vazby komunikovat přes objekty WebSockets.</span><span class="sxs-lookup"><span data-stu-id="9abce-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="9abce-104">WebSockets se použijí, když <xref:System.ServiceModel.NetHttpBinding> určí kontrakt služby, který definuje kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9abce-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="9abce-105">Toto téma popisuje, jak implementovat službu WCF a klienta, který používá <xref:System.ServiceModel.NetHttpBinding> ke komunikaci přes objekty WebSockets.</span><span class="sxs-lookup"><span data-stu-id="9abce-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="9abce-106">Definování služby</span><span class="sxs-lookup"><span data-stu-id="9abce-106">Define the Service</span></span>  
  
1. <span data-ttu-id="9abce-107">Definování kontraktu zpětného volání</span><span class="sxs-lookup"><span data-stu-id="9abce-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="9abce-108">Tato smlouva bude implementována klientskou aplikací, aby mohla služba odesílat zprávy zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="9abce-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2. <span data-ttu-id="9abce-109">Definujte kontrakt služby a určete `IStockQuoteCallback` rozhraní jako kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9abce-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3. <span data-ttu-id="9abce-110">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="9abce-110">Implement the service contract.</span></span>  
  
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
  
     <span data-ttu-id="9abce-111">Operace služby `StartSendingQuotes` je implementována jako asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="9abce-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="9abce-112">Kanál zpětného volání načteme pomocí operátoru `OperationContext` a, pokud je kanál otevřený, provádíme asynchronní volání na kanálu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9abce-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4. <span data-ttu-id="9abce-113">Konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="9abce-113">Configure the service</span></span>  
  
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
  
     <span data-ttu-id="9abce-114">Konfigurační soubor služby spoléhá na výchozí koncové body WCF.</span><span class="sxs-lookup"><span data-stu-id="9abce-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="9abce-115">`<protocolMapping>`Oddíl slouží k určení, zda má `NetHttpBinding` být použit pro výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="9abce-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="9abce-116">Definování klienta</span><span class="sxs-lookup"><span data-stu-id="9abce-116">Define the Client</span></span>  
  
1. <span data-ttu-id="9abce-117">Implementujte kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9abce-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="9abce-118">Operace kontraktu zpětného volání je implementována jako asynchronní metoda.</span><span class="sxs-lookup"><span data-stu-id="9abce-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1. <span data-ttu-id="9abce-119">Implementujte kód klienta.</span><span class="sxs-lookup"><span data-stu-id="9abce-119">Implement the client code.</span></span>  
  
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
  
         <span data-ttu-id="9abce-120">Hodnota CallbackHandler se tady opakuje pro přehlednost.</span><span class="sxs-lookup"><span data-stu-id="9abce-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="9abce-121">Klientská aplikace vytvoří novou funkci InstanceContext a určí implementaci rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9abce-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="9abce-122">V dalším kroku se vytvoří instance třídy proxy, která posílá odkaz na nově vytvořenou třídu InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="9abce-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="9abce-123">Když klient zavolá službu, služba zavolá klienta pomocí zadaného kontraktu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9abce-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2. <span data-ttu-id="9abce-124">Konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="9abce-124">Configure the client</span></span>  
  
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
  
         <span data-ttu-id="9abce-125">V konfiguraci klienta nemusíte nic dělat, stačí zadat koncový bod na straně klienta pomocí `NetHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="9abce-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9abce-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="9abce-126">Example</span></span>  
 <span data-ttu-id="9abce-127">Následuje kompletní kód, který se používá v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="9abce-127">The following is the complete code used in this topic.</span></span>  
  
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
  
```aspx-csharp
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
  
## <a name="see-also"></a><span data-ttu-id="9abce-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9abce-128">See also</span></span>

- [<span data-ttu-id="9abce-129">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="9abce-129">Synchronous and Asynchronous Operations</span></span>](../synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="9abce-130">Používání vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9abce-130">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)
