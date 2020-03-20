---
title: Korelace trvanlivého duplexního přenosu
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: bb73cef5190a0b146e713ef1adae24219dc2eed8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185177"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="442f0-102">Korelace trvanlivého duplexního přenosu</span><span class="sxs-lookup"><span data-stu-id="442f0-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="442f0-103">Trvalá duplexní korelace, označovaná také jako korelace zpětného volání, je užitečná, když služba pracovního postupu má požadavek na odeslání zpětného volání počátečnímu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="442f0-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="442f0-104">Na rozdíl od WCF duplex, zpětné volání může dojít kdykoli v budoucnu a není vázána na stejný kanál nebo životnost kanálu; jediným požadavkem je, že volající má aktivní koncový bod naslouchání pro zprávu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="442f0-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="442f0-105">To umožňuje dvě služby pracovního postupu komunikovat v dlouhotrvající konverzaci.</span><span class="sxs-lookup"><span data-stu-id="442f0-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="442f0-106">Toto téma poskytuje přehled trvalé duplexní korelace.</span><span class="sxs-lookup"><span data-stu-id="442f0-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="442f0-107">Použití trvalé oboustranné korelace</span><span class="sxs-lookup"><span data-stu-id="442f0-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="442f0-108">Chcete-li použít trvalé duplexní korelace, dvě služby musí používat vazbu s podporou kontextu, který podporuje obousměrné operace, například <xref:System.ServiceModel.NetTcpContextBinding> nebo <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="442f0-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="442f0-109">Volající služba registruje <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> s požadovanou vazbou na svého klienta <xref:System.ServiceModel.Endpoint>.</span><span class="sxs-lookup"><span data-stu-id="442f0-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="442f0-110">Přijímající služba obdrží tato data v počáteční volání a <xref:System.ServiceModel.Endpoint> potom <xref:System.ServiceModel.Activities.Send> ji používá samostatně v aktivitě, která provede volání zpět do volající služby.</span><span class="sxs-lookup"><span data-stu-id="442f0-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="442f0-111">V tomto příkladu dvě služby komunikovat mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="442f0-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="442f0-112">První služba vyvolá metodu na druhou službu a pak čeká na odpověď.</span><span class="sxs-lookup"><span data-stu-id="442f0-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="442f0-113">Druhá služba zná název metody zpětného volání, ale koncový bod služby, která implementuje tuto metodu není znám v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="442f0-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="442f0-114">Odolný duplex lze použít <xref:System.ServiceModel.Channels.AddressingVersion> pouze v případě, <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>že koncový bod je nakonfigurován s .</span><span class="sxs-lookup"><span data-stu-id="442f0-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="442f0-115">Pokud tomu tak není, je vyvolána <xref:System.InvalidOperationException> výjimka s následující zprávou: "Zpráva obsahuje hlavičku kontextu zpětného volání s odkazem na koncový bod pro [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span><span class="sxs-lookup"><span data-stu-id="442f0-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="442f0-116">Kontext zpětného volání lze přenášet pouze v případě, že AddressingVersion je nakonfigurován s 'WSAddressing10'.</span><span class="sxs-lookup"><span data-stu-id="442f0-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="442f0-117">V následujícím příkladu je hostována služba pracovního postupu, která vytvoří zpětné <xref:System.ServiceModel.Endpoint> volání pomocí <xref:System.ServiceModel.WSHttpContextBinding>aplikace .</span><span class="sxs-lookup"><span data-stu-id="442f0-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 <span data-ttu-id="442f0-118">Pracovní postup, který implementuje tuto službu pracovního <xref:System.ServiceModel.Activities.Send> postupu inicializuje korelaci zpětného volání s jeho aktivitou a odkazuje na tento koncový bod zpětného <xref:System.ServiceModel.Activities.Receive> volání z aktivity, která koreluje s <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="442f0-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="442f0-119">Následující příklad představuje pracovní postup, `GetWF1` který je vrácen z metody.</span><span class="sxs-lookup"><span data-stu-id="442f0-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="442f0-120">Druhá služba pracovního postupu je hostována pomocí systémově poskytované kontextové vazby.</span><span class="sxs-lookup"><span data-stu-id="442f0-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 <span data-ttu-id="442f0-121">Pracovní postup, který implementuje tuto <xref:System.ServiceModel.Activities.Receive> službu pracovního postupu, začíná aktivitou.</span><span class="sxs-lookup"><span data-stu-id="442f0-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="442f0-122">Tato aktivita příjmu inicializuje korelaci zpětného volání pro tuto službu, zpozdí po určitou dobu simulovat dlouhotrvající práci a pak zavolá zpět do první služby pomocí kontextu zpětného volání, který byl předán v prvním volání do služby.</span><span class="sxs-lookup"><span data-stu-id="442f0-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="442f0-123">Následující příklad představuje pracovní postup, který `GetWF2`je vrácen z volání do aplikace .</span><span class="sxs-lookup"><span data-stu-id="442f0-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="442f0-124">Všimněte <xref:System.ServiceModel.Activities.Send> si, že aktivita `http://www.contoso.com`má zástupnou adresu ; skutečná adresa použitá za běhu je zadaná adresa zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="442f0-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="442f0-125">Při `StartOrder` vyvolání metody v prvním pracovním postupu se zobrazí následující výstup, který zobrazuje tok provádění prostřednictvím dvou pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="442f0-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 <span data-ttu-id="442f0-126">V tomto příkladu oba pracovní postupy <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>explicitně spravovat korelaci pomocí .</span><span class="sxs-lookup"><span data-stu-id="442f0-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="442f0-127">Vzhledem k tomu, že v těchto ukázkových pracovních postupech byla pouze jedna korelace, výchozí <xref:System.ServiceModel.Activities.CorrelationHandle> správa by byla dostatečná.</span><span class="sxs-lookup"><span data-stu-id="442f0-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
