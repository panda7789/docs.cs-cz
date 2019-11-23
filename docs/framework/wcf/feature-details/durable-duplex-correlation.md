---
title: Korelace trvanlivého duplexního přenosu
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: efc647b8a39f419f2165fe355529ba145663b753
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291576"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="9dcff-102">Korelace trvanlivého duplexního přenosu</span><span class="sxs-lookup"><span data-stu-id="9dcff-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="9dcff-103">Trvalá korelace, označovaná také jako korelace zpětného volání, je užitečná v případě, že služba pracovního postupu má požadavek na odeslání zpětného volání počátečnímu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="9dcff-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="9dcff-104">Na rozdíl od služby WCF Duplex může zpětné volání probíhat kdykoli v budoucnu a není vázáno na stejný kanál nebo na životnost kanálu; Jediným požadavkem je, že volající má aktivní koncový bod pro zprávu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9dcff-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="9dcff-105">To umožňuje, aby dvě služby pracovních postupů komunikovaly s dlouhou běžící konverzací.</span><span class="sxs-lookup"><span data-stu-id="9dcff-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="9dcff-106">Toto téma poskytuje přehled odolné duplexní korelace.</span><span class="sxs-lookup"><span data-stu-id="9dcff-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="9dcff-107">Použití odolné duplexní korelace</span><span class="sxs-lookup"><span data-stu-id="9dcff-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="9dcff-108">Chcete-li použít odolnou duplexní korelaci, musí tyto dvě služby používat kontextově povolenou vazbu, která podporuje dvoucestné operace, například <xref:System.ServiceModel.NetTcpContextBinding> nebo <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="9dcff-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="9dcff-109">Volající služba zaregistruje <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> s požadovanou vazbou pro klientské <xref:System.ServiceModel.Endpoint>.</span><span class="sxs-lookup"><span data-stu-id="9dcff-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="9dcff-110">Přijímající služba obdrží tato data při počátečním volání a pak ji použije na vlastní <xref:System.ServiceModel.Endpoint> v aktivitě <xref:System.ServiceModel.Activities.Send>, která volá zpět do volající služby.</span><span class="sxs-lookup"><span data-stu-id="9dcff-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="9dcff-111">V tomto příkladu vzájemně komunikují dvě služby.</span><span class="sxs-lookup"><span data-stu-id="9dcff-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="9dcff-112">První služba vyvolá metodu u druhé služby a potom počká na odpověď.</span><span class="sxs-lookup"><span data-stu-id="9dcff-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="9dcff-113">Druhá služba zná název metody zpětného volání, ale koncový bod služby, který implementuje tuto metodu, není v době návrhu znám.</span><span class="sxs-lookup"><span data-stu-id="9dcff-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dcff-114">Trvalý duplexní přenos lze použít, pouze pokud je <xref:System.ServiceModel.Channels.AddressingVersion> koncového bodu nakonfigurován s <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span><span class="sxs-lookup"><span data-stu-id="9dcff-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="9dcff-115">Pokud není, je vyvolána výjimka <xref:System.InvalidOperationException> s následující zprávou: "zpráva obsahuje hlavičku kontextu zpětného volání s referencí koncového bodu pro [verze AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span><span class="sxs-lookup"><span data-stu-id="9dcff-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="9dcff-116">Kontext zpětného volání lze přenést pouze v případě, že je verze AddressingVersion nakonfigurován pomocí ' třídy WSAddressing10 '.</span><span class="sxs-lookup"><span data-stu-id="9dcff-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="9dcff-117">V následujícím příkladu je hostovaná služba pracovního postupu, která vytvoří zpětné volání <xref:System.ServiceModel.Endpoint> pomocí <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="9dcff-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
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
  
 <span data-ttu-id="9dcff-118">Pracovní postup, který implementuje tuto službu pracovního postupu, inicializuje korelaci zpětného volání s aktivitou <xref:System.ServiceModel.Activities.Send> a odkazuje na tento koncový bod zpětného volání z aktivity <xref:System.ServiceModel.Activities.Receive>, která se koreluje s <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="9dcff-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="9dcff-119">Následující příklad představuje pracovní postup, který je vrácen z metody `GetWF1`.</span><span class="sxs-lookup"><span data-stu-id="9dcff-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
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
  
 <span data-ttu-id="9dcff-120">Druhá služba pracovního postupu je hostovaná pomocí kontextové vazby založené na systému.</span><span class="sxs-lookup"><span data-stu-id="9dcff-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
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
  
 <span data-ttu-id="9dcff-121">Pracovní postup, který implementuje tuto službu pracovního postupu, začíná <xref:System.ServiceModel.Activities.Receive> aktivitou.</span><span class="sxs-lookup"><span data-stu-id="9dcff-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="9dcff-122">Tato aktivita Receive inicializuje korelaci zpětného volání pro tuto službu, zpoždění po určitou dobu pro simulaci dlouhotrvající práce a pak zavolá zpět do první služby pomocí kontextu zpětného volání, který byl předán do služby v prvním volání.</span><span class="sxs-lookup"><span data-stu-id="9dcff-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="9dcff-123">Následující příklad představuje pracovní postup, který je vrácen voláním `GetWF2`.</span><span class="sxs-lookup"><span data-stu-id="9dcff-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="9dcff-124">Všimněte si, že aktivita <xref:System.ServiceModel.Activities.Send> má zástupnou adresu `http://www.contoso.com`; Skutečná adresa používaná za běhu je dodaná adresa zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9dcff-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
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
  
 <span data-ttu-id="9dcff-125">Při vyvolání metody `StartOrder` v prvním pracovním postupu se zobrazí následující výstup, který ukazuje tok provádění prostřednictvím těchto dvou pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="9dcff-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
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
  
 <span data-ttu-id="9dcff-126">V tomto příkladu oba pracovní postupy explicitně spravují korelační pomocí <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="9dcff-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="9dcff-127">Vzhledem k tomu, že v těchto ukázkových pracovních postupech existovala jenom jedna korelace, měla by být výchozí Správa <xref:System.ServiceModel.Activities.CorrelationHandle> dostatečná.</span><span class="sxs-lookup"><span data-stu-id="9dcff-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
