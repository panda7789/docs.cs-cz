---
title: "Korelace trvanlivého duplexního přenosu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9371729dcac22b0611f8ea3ec29cc59daf5d67b8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="durable-duplex-correlation"></a>Korelace trvanlivého duplexního přenosu
Korelace trvanlivého duplexního přenosu, také známé jako zpětné volání korelace, je užitečné, když služby pracovního postupu se poslat počáteční volající zpětné volání. Na rozdíl od duplexní režim WCF může dojít kdykoliv v budoucnu zpětné volání a není vázaný na stejném kanálu nebo kanálu životnost; Jediným požadavkem je, že volající mít aktivní koncový bod naslouchání pro zpětné volání zprávy. To umožňuje dvou služeb pracovních postupů pro komunikaci v rámci dlouhodobé konverzace. Toto téma obsahuje přehled korelace trvanlivého duplexního přenosu.  
  
## <a name="using-durable-duplex-correlation"></a>Pomocí korelace trvanlivého duplexního přenosu  
 Korelace trvanlivého duplexního přenosu, dvě služby vyžaduje použití kontextu povoleno vazbu, která podporuje obousměrný operace, jako například <xref:System.ServiceModel.NetTcpContextBinding> nebo <xref:System.ServiceModel.WSHttpContextBinding>. Volání služby Registry <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> s požadovanou vazbu na jejich klienta <xref:System.ServiceModel.Endpoint>. Služba přijímající obdrží tato data ve počáteční volání a používá ho na svůj vlastní <xref:System.ServiceModel.Endpoint> v <xref:System.ServiceModel.Activities.Send> aktivity, která provádí volání zpět do volání služby. V tomto příkladu dvě služby komunikaci mezi sebou. První službě vyvolá metodu na druhý služby a pak se čeká na odpověď. Druhý služba ví název metody zpětného volání, ale koncový bod služby, která implementuje tuto metodu není znám. v době návrhu.  
  
> [!NOTE]
>  Trvanlivý duplexní přenos může být pouze použít, když <xref:System.ServiceModel.Channels.AddressingVersion> koncového bodu je nakonfigurován s <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Pokud není, pak <xref:System.InvalidOperationException> je vyvolána výjimka s následující zprávou: "zpráva obsahuje hlavičku zpětného volání kontextu se odkaz na koncový bod pro třídu AddressingVersion ' Addressing200408 (HYPERLINK"http://schemas.xmlsoap.org/ws/2004/08/ adresování"http://schemas.xmlsoap.org/ws/2004/08/addressing)'. Zpětné volání kontextu může být přenášen pouze v případě nastavena třídu AddressingVersion 'WSAddressing10'."  
  
 V následujícím příkladu je hostované služby pracovního postupu, vytvoří zpětné volání <xref:System.ServiceModel.Endpoint> pomocí <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Pracovní postup, který implementuje této služby pracovního postupu inicializuje korelace zpětné volání s jeho <xref:System.ServiceModel.Activities.Send> aktivitu a odkazuje na tento koncový bod zpětného volání z <xref:System.ServiceModel.Activities.Receive> aktivity, které koreluje s <xref:System.ServiceModel.Activities.Send>. V následujícím příkladu představuje pracovní postup, který je vrácen z `GetWF1` metoda.  
  
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
  
 Druhý služby pracovního postupu je hostován použití poskytované systémem, na základě kontextu vazby.  
  
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
  
 Pracovní postup, který implementuje tuto službu pracovní postup začíná <xref:System.ServiceModel.Activities.Receive> aktivity. To přijímat aktivity inicializuje korelace zpětného volání pro tuto službu, zpoždění dobu simulovat dlouhotrvající práci a pak volání zpět do první služby v kontextu zpětného volání, který byl předán při prvním volání do služby. V následujícím příkladu představuje pracovní postup, který je vrácená z volání `GetWF2`. Všimněte si, že <xref:System.ServiceModel.Activities.Send> aktivita má adresu zástupný symbol `http://www.contoso.com`; skutečná adresa použitá v době běhu je adresa zadaná zpětného volání.  
  
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
  
 Když `StartOrder` metoda je volána pro první pracovní postup, se zobrazí následující výstup, který zobrazuje tok provádění prostřednictvím dvou pracovních postupů.  
  
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
  
 V tomto příkladu obou pracovních explicitně spravovat pomocí korelace <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Kvůli pouze jeden korelace v pracovních postupech tyto ukázkové, výchozí <xref:System.ServiceModel.Activities.CorrelationHandle> správy by byl dostatečná.  
  
## <a name="see-also"></a>Viz také  
 [Trvanlivý duplexní přenos &#91; Ukázky WF &#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
