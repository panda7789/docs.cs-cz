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
# <a name="durable-duplex-correlation"></a>Korelace trvanlivého duplexního přenosu
Trvalá duplexní korelace, označovaná také jako korelace zpětného volání, je užitečná, když služba pracovního postupu má požadavek na odeslání zpětného volání počátečnímu volajícímu. Na rozdíl od WCF duplex, zpětné volání může dojít kdykoli v budoucnu a není vázána na stejný kanál nebo životnost kanálu; jediným požadavkem je, že volající má aktivní koncový bod naslouchání pro zprávu zpětného volání. To umožňuje dvě služby pracovního postupu komunikovat v dlouhotrvající konverzaci. Toto téma poskytuje přehled trvalé duplexní korelace.  
  
## <a name="using-durable-duplex-correlation"></a>Použití trvalé oboustranné korelace  
 Chcete-li použít trvalé duplexní korelace, dvě služby musí používat vazbu s podporou kontextu, který podporuje obousměrné operace, například <xref:System.ServiceModel.NetTcpContextBinding> nebo <xref:System.ServiceModel.WSHttpContextBinding>. Volající služba registruje <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> s požadovanou vazbou na svého klienta <xref:System.ServiceModel.Endpoint>. Přijímající služba obdrží tato data v počáteční volání a <xref:System.ServiceModel.Endpoint> potom <xref:System.ServiceModel.Activities.Send> ji používá samostatně v aktivitě, která provede volání zpět do volající služby. V tomto příkladu dvě služby komunikovat mezi sebou. První služba vyvolá metodu na druhou službu a pak čeká na odpověď. Druhá služba zná název metody zpětného volání, ale koncový bod služby, která implementuje tuto metodu není znám v době návrhu.  
  
> [!NOTE]
> Odolný duplex lze použít <xref:System.ServiceModel.Channels.AddressingVersion> pouze v případě, <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>že koncový bod je nakonfigurován s . Pokud tomu tak není, je vyvolána <xref:System.InvalidOperationException> výjimka s následující zprávou: "Zpráva obsahuje hlavičku kontextu zpětného volání s odkazem na koncový bod pro [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing). Kontext zpětného volání lze přenášet pouze v případě, že AddressingVersion je nakonfigurován s 'WSAddressing10'.
  
 V následujícím příkladu je hostována služba pracovního postupu, která vytvoří zpětné <xref:System.ServiceModel.Endpoint> volání pomocí <xref:System.ServiceModel.WSHttpContextBinding>aplikace .  
  
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
  
 Pracovní postup, který implementuje tuto službu pracovního <xref:System.ServiceModel.Activities.Send> postupu inicializuje korelaci zpětného volání s jeho aktivitou a odkazuje na tento koncový bod zpětného <xref:System.ServiceModel.Activities.Receive> volání z aktivity, která koreluje s <xref:System.ServiceModel.Activities.Send>. Následující příklad představuje pracovní postup, `GetWF1` který je vrácen z metody.  
  
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
  
 Druhá služba pracovního postupu je hostována pomocí systémově poskytované kontextové vazby.  
  
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
  
 Pracovní postup, který implementuje tuto <xref:System.ServiceModel.Activities.Receive> službu pracovního postupu, začíná aktivitou. Tato aktivita příjmu inicializuje korelaci zpětného volání pro tuto službu, zpozdí po určitou dobu simulovat dlouhotrvající práci a pak zavolá zpět do první služby pomocí kontextu zpětného volání, který byl předán v prvním volání do služby. Následující příklad představuje pracovní postup, který `GetWF2`je vrácen z volání do aplikace . Všimněte <xref:System.ServiceModel.Activities.Send> si, že aktivita `http://www.contoso.com`má zástupnou adresu ; skutečná adresa použitá za běhu je zadaná adresa zpětného volání.  
  
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
  
 Při `StartOrder` vyvolání metody v prvním pracovním postupu se zobrazí následující výstup, který zobrazuje tok provádění prostřednictvím dvou pracovních postupů.  
  
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
  
 V tomto příkladu oba pracovní postupy <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>explicitně spravovat korelaci pomocí . Vzhledem k tomu, že v těchto ukázkových pracovních postupech byla pouze jedna korelace, výchozí <xref:System.ServiceModel.Activities.CorrelationHandle> správa by byla dostatečná.
