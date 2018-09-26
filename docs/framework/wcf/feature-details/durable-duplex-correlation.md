---
title: Korelace trvanlivého duplexního přenosu
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: 82c052ff87eb8b125dfc64e1567dbd00d255894d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079620"
---
# <a name="durable-duplex-correlation"></a>Korelace trvanlivého duplexního přenosu
Korelace trvanlivého duplexního přenosu, označované také jako zpětné volání korelace, je užitečné, když služba pracovního postupu má požadavek na odeslání zpětné volání počáteční volajícímu. Na rozdíl od WCF duplexní zpětného volání v každém okamžiku v budoucnu se může stát a není vázaný na jeden kanál nebo kanál životnost; Jediným požadavkem je, že volající mít aktivní koncový bod naslouchání pro zpětné volání zprávy. To umožňuje dvě služby pracovního postupu pro komunikaci v rámci dlouhotrvající konverzace. Toto téma obsahuje přehled korelace trvanlivého duplexního přenosu.  
  
## <a name="using-durable-duplex-correlation"></a>Pomocí korelace trvanlivého duplexního přenosu  
 Korelace trvanlivého duplexního přenosu, tyto dvě služby vyžaduje použití vazbu povolen kontext, která podporuje obousměrné operace, jako například <xref:System.ServiceModel.NetTcpContextBinding> nebo <xref:System.ServiceModel.WSHttpContextBinding>. Volání služby registrů <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> požadované vazby v klientovi <xref:System.ServiceModel.Endpoint>. Přijímající služba obdrží tato data v počáteční volání a pak pomocí něj sama o sobě <xref:System.ServiceModel.Endpoint> v <xref:System.ServiceModel.Activities.Send> aktivitu, která provádí volání zpět do volání služby. V tomto příkladu dvě služby vzájemně komunikují. První služba volá metodu na druhý služby a poté počká na odpověď. Druhá služba ví název metody zpětného volání, ale koncový bod služby, která implementuje tuto metodu není znám v době návrhu.  
  
> [!NOTE]
> Trvanlivý duplexní přenos může obsahovat jenom nepoužívá, pokud <xref:System.ServiceModel.Channels.AddressingVersion> koncového bodu má nakonfigurovanou <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Pokud ne, pak <xref:System.InvalidOperationException> je vyvolána výjimka s následující zprávou: "zpráva obsahuje hlavičku kontextu zpětného volání s odkazem na koncový bod pro [verze AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing). Kontext zpětného volání lze přenášet pouze, pokud verze AddressingVersion konfigurována s "Třídy WSAddressing10".
  
 V následujícím příkladu je hostované služby pracovního postupu, který vytvoří zpětné volání <xref:System.ServiceModel.Endpoint> pomocí <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Pracovní postup, který implementuje tato služba pracovního postupu inicializuje korelaci zpětného volání s jeho <xref:System.ServiceModel.Activities.Send> aktivitu a odkazuje na tento koncový bod zpětného volání z <xref:System.ServiceModel.Activities.Receive> aktivitu, která koreluje s <xref:System.ServiceModel.Activities.Send>. Následující příklad představuje pracovní postup, který je vrácen z `GetWF1` metody.  
  
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
  
 Druhá služba pracovního postupu je hostované pomocí poskytnuté systémem, na základě kontextu vazby.  
  
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
  
 Pracovní postup, který implementuje tato služba pracovního postupu začíná <xref:System.ServiceModel.Activities.Receive> aktivity. To přijímat aktivity inicializuje korelaci zpětného volání pro tuto službu prodlevy pro určité době simulovat dlouhotrvající práci a poté zavolá zpět do první service pomocí kontextu zpětného volání, který byl předán při prvním volání do služby. Následující příklad představuje pracovní postup, který je vrácen z volání `GetWF2`. Všimněte si, že <xref:System.ServiceModel.Activities.Send> adresu zástupný symbol má aktivita `http://www.contoso.com`; skutečná adresa používá za běhu je adresa zadaná zpětného volání.  
  
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
  
 Když `StartOrder` metoda se vyvolá u prvního pracovního postupu, se zobrazí následující výstup, který znázorňuje tok spuštění prostřednictvím dvou pracovních postupů.  
  
```Output  
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
  
 V tomto příkladu obou pracovních postupů explicitně spravovat pomocí korelace <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Protože pouze jeden korelace v pracovních postupech tyto ukázky, výchozí <xref:System.ServiceModel.Activities.CorrelationHandle> správy by byl dostatečná.  
  
## <a name="see-also"></a>Viz také  
 [Trvanlivý duplexní přenos &#91;ukázky WF&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
