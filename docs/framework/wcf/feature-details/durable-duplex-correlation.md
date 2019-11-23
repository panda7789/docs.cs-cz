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
# <a name="durable-duplex-correlation"></a>Korelace trvanlivého duplexního přenosu
Trvalá korelace, označovaná také jako korelace zpětného volání, je užitečná v případě, že služba pracovního postupu má požadavek na odeslání zpětného volání počátečnímu volajícímu. Na rozdíl od služby WCF Duplex může zpětné volání probíhat kdykoli v budoucnu a není vázáno na stejný kanál nebo na životnost kanálu; Jediným požadavkem je, že volající má aktivní koncový bod pro zprávu zpětného volání. To umožňuje, aby dvě služby pracovních postupů komunikovaly s dlouhou běžící konverzací. Toto téma poskytuje přehled odolné duplexní korelace.  
  
## <a name="using-durable-duplex-correlation"></a>Použití odolné duplexní korelace  
 Chcete-li použít odolnou duplexní korelaci, musí tyto dvě služby používat kontextově povolenou vazbu, která podporuje dvoucestné operace, například <xref:System.ServiceModel.NetTcpContextBinding> nebo <xref:System.ServiceModel.WSHttpContextBinding>. Volající služba zaregistruje <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> s požadovanou vazbou pro klientské <xref:System.ServiceModel.Endpoint>. Přijímající služba obdrží tato data při počátečním volání a pak ji použije na vlastní <xref:System.ServiceModel.Endpoint> v aktivitě <xref:System.ServiceModel.Activities.Send>, která volá zpět do volající služby. V tomto příkladu vzájemně komunikují dvě služby. První služba vyvolá metodu u druhé služby a potom počká na odpověď. Druhá služba zná název metody zpětného volání, ale koncový bod služby, který implementuje tuto metodu, není v době návrhu znám.  
  
> [!NOTE]
> Trvalý duplexní přenos lze použít, pouze pokud je <xref:System.ServiceModel.Channels.AddressingVersion> koncového bodu nakonfigurován s <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Pokud není, je vyvolána výjimka <xref:System.InvalidOperationException> s následující zprávou: "zpráva obsahuje hlavičku kontextu zpětného volání s referencí koncového bodu pro [verze AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing). Kontext zpětného volání lze přenést pouze v případě, že je verze AddressingVersion nakonfigurován pomocí ' třídy WSAddressing10 '.
  
 V následujícím příkladu je hostovaná služba pracovního postupu, která vytvoří zpětné volání <xref:System.ServiceModel.Endpoint> pomocí <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Pracovní postup, který implementuje tuto službu pracovního postupu, inicializuje korelaci zpětného volání s aktivitou <xref:System.ServiceModel.Activities.Send> a odkazuje na tento koncový bod zpětného volání z aktivity <xref:System.ServiceModel.Activities.Receive>, která se koreluje s <xref:System.ServiceModel.Activities.Send>. Následující příklad představuje pracovní postup, který je vrácen z metody `GetWF1`.  
  
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
  
 Druhá služba pracovního postupu je hostovaná pomocí kontextové vazby založené na systému.  
  
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
  
 Pracovní postup, který implementuje tuto službu pracovního postupu, začíná <xref:System.ServiceModel.Activities.Receive> aktivitou. Tato aktivita Receive inicializuje korelaci zpětného volání pro tuto službu, zpoždění po určitou dobu pro simulaci dlouhotrvající práce a pak zavolá zpět do první služby pomocí kontextu zpětného volání, který byl předán do služby v prvním volání. Následující příklad představuje pracovní postup, který je vrácen voláním `GetWF2`. Všimněte si, že aktivita <xref:System.ServiceModel.Activities.Send> má zástupnou adresu `http://www.contoso.com`; Skutečná adresa používaná za běhu je dodaná adresa zpětného volání.  
  
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
  
 Při vyvolání metody `StartOrder` v prvním pracovním postupu se zobrazí následující výstup, který ukazuje tok provádění prostřednictvím těchto dvou pracovních postupů.  
  
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
  
 V tomto příkladu oba pracovní postupy explicitně spravují korelační pomocí <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Vzhledem k tomu, že v těchto ukázkových pracovních postupech existovala jenom jedna korelace, měla by být výchozí Správa <xref:System.ServiceModel.Activities.CorrelationHandle> dostatečná.
